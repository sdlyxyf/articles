## DjangoRESTFramework的学习笔记：
教程“大江狗的博客”：https://pythondjango.cn/django/rest-framework-tutorials
1,使用FBV和CBV方式来实现，分别见fbv_views.py和cbv_views.py; 通用api接口建议使用CBV的generics类，代码简洁。 
2，使用generics类中的方法，只需要设定queeyset,serializer_class,permission_classes,authentication_classes  
3，权限：使用IsAuthenticated，注册用户登录后才可以操作。  
4，认证：使用自带的token认证方式。在setting中添加rest_framework.authtoken模块，在urls中设定URL，  
使用 post http://localhost:8000/api-token-auth/ 带用户登录信息可以获取token，  
token信息存在在token表中，需要命令行 ./manage.py drf_create_token <username> # 新建；  
./manage.py drf_create_token -r <username> # 重置生成。  
5，客户端拿到token后可以将其存储到本地cookie或localstorage里，下次发送请求时把token包含在Authorization HTTP头即可，如下所示：  
 { Authorization: Token 9944b09199c62bcf9418ad846dd0e4bbdfc6ee4b} 此处应特别注意token带入的格式 。
 token带入的用户信息，由request.user获取，注意写入数据表的方式：serializer.save(author=request.user)  
6, 使用requests进行测试，见api_test.py; 对api的使用，可见api_axios_test.html页面的演示。  
7，对应get、post、put、delete方式发送的数据，根据param、data、hearde部位的不同对应request.GET,request.POST,request.body,request.data  
8，对于跨域问题，使用django-cors-headers模块进行处理，详见有关介绍。  
9，没有使用JWT方式。没有涉及到过滤和分流。
10,method中put和patch方法的区别，put用于对全字段的修改，patch用于对单独字段的修改。经测试，put修改单个字段时会报错。

#  具体代码：<
1、数据模型：models.py
class Article(models.Model):  
    STATUS_CHOICES = (('p','Published'),('d','Draft'))  
    title=models.CharField(verbose_name='Title',max_length=60,db_index=True)  
    body=models.TextField(verbose_name='Body',blank=True)  
    author=models.CharField(verbose_name='Author',max_length=20,null=True,blank=True)     status=models.CharField(verbose_name='Status',max_length=1,choices=STATUS_CHOICES,default='d',null=True,blank=True)  
    create_date=models.DateTimeField(verbose_name='Create Date',auto_now_add=True)  
    update_date=models.DateTimeField(verbose_name='Update Date',auto_now=True)
2、序列化模型：serializers.py
from rest_framework import serializers  
from .models import Article    
class ArticleSerializer(serializers.ModelSerializer):  
		 class Meta:  
				 model=Article  
				 fields='__all__'  
				 read_only_fields=('id','create_date','update_date')
 3、项目根目录urls.py中的url设定：
 path('api-auth/', include('rest_framework.urls')), # 用户登录页面  
 path('api-token-auth/',token_views.obtain_auth_token), #使用rest自带的token认证方式，用户token请求，post方法带用户登录信息
 4、app中urls.py中的url设定：
    re_path(r'^f-articles/$', fbv_views.article_list),  
	re_path(r'^f-articles/(?P<pk>[0-9]+)$', fbv_views.article_detail),  
	re_path(r'^c-articles/$', cbv_views.ArticleList.as_view()),  
	re_path(r'^c-articles/(?P<pk>[0-9]+)$', cbv_views.ArticleDetail.as_view()),
5、FBV模式下的views.py代码：
# FBV
from rest_framework import status
from rest_framework.decorators import api_view,permission_classes,authentication_classes
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response
from rest_framework.authentication import TokenAuthentication
from .models import Article
from .serializers import ArticleSerializer


@api_view(['GET', 'POST'])
@permission_classes((IsAuthenticated,)) #权限类别
@authentication_classes((TokenAuthentication,)) #认证方式
def article_list(request):
    """
    List all articles, or create a new article.
    """
    if request.method == 'GET':
        articles = Article.objects.all()
        serializer = ArticleSerializer(articles, many=True)
        return Response(serializer.data)

    elif request.method == 'POST':
        serializer = ArticleSerializer(data=request.data)
        if serializer.is_valid():
            # Very important. Associate request.user with author
            serializer.save(author=request.user)
            return Response(serializer.data, status=status.HTTP_201_CREATED)
        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)


@api_view(['GET', 'PUT', 'DELETE'])
@permission_classes((IsAuthenticated,)) #权限类别
@authentication_classes((TokenAuthentication,)) #认证方式
def article_detail(request, pk):
    """
    Retrieve，update or delete an article instance。"""
    try:
        article = Article.objects.get(pk=pk)
    except Article.DoesNotExist:
        return Response(status=status.HTTP_404_NOT_FOUND)

    if request.method == 'GET':
        serializer = ArticleSerializer(article)
        return Response(serializer.data)

    elif request.method == 'PUT':
        serializer = ArticleSerializer(article, data=request.data)
        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data)
        return Response(serializer.errors, status=status.HTTP_400_BAD_REQUEST)

    elif request.method == 'DELETE':
        article.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)

6、CBV模式下的views.py代码：
# generic class-based views
from rest_framework import generics
from rest_framework import permissions
from rest_framework.authentication import TokenAuthentication
from .models import Article
from .serializers import ArticleSerializer

class ArticleList(generics.ListCreateAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
    permission_classes = (permissions.IsAuthenticated,) #限制只有注册用户才能操作
    authentication_classes = (TokenAuthentication,) #认证方式为Token

    # 将request.user与author绑定,由token带入用户登录信息
    def perform_create(self, serializer):
        serializer.save(author=self.request.user)

class ArticleDetail(generics.RetrieveUpdateDestroyAPIView):
    queryset = Article.objects.all()
    serializer_class =ArticleSerializer
    permission_classes = (permissions.IsAuthenticated,) #限制只有注册用户才能操作
    authentication_classes = (TokenAuthentication,) #认证方式为Token

7、使用requests对api接口进行测试：
代码：
import requests
import json

TOKEN_STR='' # token字符串，全局变量

def get_token(data=None):
    global TOKEN_STR
    url="http://localhost:8000/api-token-auth/"
    data={"username":"admin","password":"1234"}
    res=requests.post(url,data=data)
    # print(res.text)
    res_dict=json.loads(res.text)
    TOKEN_STR=res_dict['token']
    return TOKEN_STR

def get_articles(pk=None):
    global TOKEN_STR
    if pk==None:
        url="http://localhost:8000/blog/c-articles/"
    else:
        url = "http://localhost:8000/blog/c-articles/"+str(pk)
    if TOKEN_STR=='':
        TOKEN_STR=get_token()
    headers = {'Authorization': 'Token {}'.format(TOKEN_STR)}  # token的认证方式
    res = requests.get(url, headers=headers)
    print(res.text)
    return res.status_code

def post_article(data=None):
    global TOKEN_STR
    if TOKEN_STR=='':
        TOKEN_STR=get_token()
    url = "http://localhost:8000/blog/c-articles/"
    headers = {'Authorization': 'Token {}'.format(TOKEN_STR)}  # token的认证方式
    res = requests.post(url, headers=headers,data=data)
    return res.status_code

def delete_article(pk=None):
    global TOKEN_STR
    if TOKEN_STR == '':
        TOKEN_STR = get_token()
    url = "http://localhost:8000/blog/c-articles/"+str(pk)
    headers = {'Authorization': 'Token {}'.format(TOKEN_STR)}  # token的认证方式
    res = requests.delete(url, headers=headers)
    print(res.status_code)
    return res.status_code

def patch_article(pk,data): # 更该数据，如果只列出某个字段使用patch，put方法需要列出所有字段。
    global TOKEN_STR
    if TOKEN_STR == '':
        TOKEN_STR = get_token()
    url = "http://localhost:8000/blog/c-articles/"+str(pk)
    headers = {'Authorization': 'Token {}'.format(TOKEN_STR)}  # token的认证方式
    res = requests.patch(url, headers=headers,data=data)
    print(res.status_code)
    return res.status_code  >


<>


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA2MTU2MTVdfQ==
-->