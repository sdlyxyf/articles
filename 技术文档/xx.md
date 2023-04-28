##  Django documentation:
### How the documentation is organized
Django has a lot of documentation. A high-level overview of how it's organized will help you know where to look for certain things:
+ Tutorials take you by the hand through a series of steps to create a Web application. Start here if you're new to Django or Web application development. Also look at the “First steps” below.
+ Topic guides discuss key topics and concepts at a fairly high level and provide useful background information and explanation.
+ Reference guides contain technical reference for APIs and other aspects of Django's machinery. They describe how it works and how to use it but assume that you have a basic understanding of key concepts.
+ How-to guides are recipes. They guide you through the steps involved in addressing key problems and use-cases. They are more advanced than tutorials and assume some knowledge of how Django works.

Django provides an abstraction layer (the “models”) for structuring and manipulating the data of your Web application. Learn more about it below:
Django has the concept of “views” to encapsulate the logic responsible for processing a user's request and for returning the response. Find all you need to know about views via the links below:
The template layer provides a designer-friendly syntax for rendering the information to be presented to the user. Learn how this syntax can be used by designers and how it can be extended by programmers:
Django provides a rich framework to facilitate the creation of forms and the manipulation of form data.
The development process:Learn about the various components and tools to help you in the development and testing of Django applications:
Find all you need to know about the automated admin interface, one of Django`s most popular features:
Security is a topic of paramount importance in the development of Web applications and Django provides multiple protection tools and mechanisms:
Django offers a robust internationalization and localization framework to assist you in the development of applications for multiple languages and world regions:
Performance and optimization:There are a variety of techniques and tools that can help get your code running more efficiently - faster, and using fewer system resources.
Geographic framework:GeoDjango intends to be a world-class geographic Web framework. Its goal is to make it as easy as possible to build GIS Web applications and harness the power of spatially enabled data.
Common Web application tools : Django offers multiple tools commonly needed in the development of Web applications:
Other core functionalities :Learn about some other core functionalities of the Django framework:
The Django open-source project :Learn about the development process for the Django project itself and about how you can contribute:

Getting started
New to Django? Or to Web development in general? Well, you came to the right place: read this material to quickly get up and running.
Django at a glance,Quick install guide,Advanced tutorial: How to write reusable apps,What to read next,Writing your first patch for Django
See also:If you’re new to Python, you might want to start by getting an idea of what the language is like. Django is 100% Python, so if you’ve got minimal comfort with Python you’ll probably get a lot more out of Django.
If you’re new to programming entirely, you might want to start with this list of Python resources for non-programmers
If you already know a few other languages and want to get up to speed with Python quickly, we recommend Dive Into Python. If that’s not quite your style, there are many other books about Python.
Django at a glance
Because Django was developed in a fast-paced newsroom environment, it was designed to make common Web-development tasks fast and easy. Here’s an informal overview of how to write a database-driven Web app with Django.
The goal of this document is to give you enough technical specifics to understand how Django works, but this isn’t intended to be a tutorial or reference – but we’ve got both! When you’re ready to start a project, you can start with the tutorial or dive right into more detailed documentation.
Design your model
Although you can use Django without a database, it comes with an object-relational mapper in which you describe your database layout in Python code.
The data-model syntax offers many rich ways of representing your models – so far, it’s been solving many years’ worth of database-schema problems. Here’s a quick example:
Install it
Next, run the Django command-line utility to create the database tables automatically:$ python manage.py migrate
The migrate command looks at all your available models and creates tables in your database for whichever tables don’t already exist, as well as optionally providing much richer schema control.
Enjoy the free API
With that, you’ve got a free, and rich, Python API to access your data. The API is created on the fly, no code generation necessary:
A dynamic admin interface: it’s not just scaffolding – it’s the whole house
Once your models are defined, Django can automatically create a professional, production ready administrative interface – a website that lets authenticated users add, change and delete objects. It’s as easy as registering your model in the admin site:
The philosophy here is that your site is edited by a staff, or a client, or maybe just you – and you don’t want to have to deal with creating backend interfaces just to manage content.

One typical workflow in creating Django apps is to create models and get the admin sites up and running as fast as possible, so your staff (or clients) can start populating data. Then, develop the way data is presented to the public.
Design your URLs
A clean, elegant URL scheme is an important detail in a high-quality Web application. Django encourages beautiful URL design and doesn’t put any cruft in URLs, like .php or .asp.
To design URLs for an app, you create a Python module called a URLconf. A table of contents for your app, it contains a simple mapping between URL patterns and Python callback functions. URLconfs also serve to decouple URLs from Python code.
Here’s what a URLconf might look like for the Reporter/Article example above:
The code above maps URL paths to Python callback functions (“views”). The path strings use parameter tags to “capture” values from the URLs. When a user requests a page, Django runs through each path, in order, and stops at the first one that matches the requested URL. (If none of them matches, Django calls a special-case 404 view.) This is blazingly fast, because the paths are compiled into regular expressions at load time.
Once one of the URL patterns matches, Django calls the given view, which is a Python function. Each view gets passed a request object – which contains request metadata – and the values captured in the pattern.
For example, if a user requested the URL “/articles/2005/05/39323/”, Django would call the function news.views.article_detail(request, year=2005, month=5, pk=39323).
Write your views
Each view is responsible for doing one of two things: Returning an HttpResponse object containing the content for the requested page, or raising an exception such as Http404. The rest is up to you.
Generally, a view retrieves data according to the parameters, loads a template and renders the template with the retrieved data. Here’s an example view for year_archive from above:
This example uses Django’s template system, which has several powerful features but strives to stay simple enough for non-programmers to use.
Design your templates
The code above loads the news/year_archive.html template.
Django has a template search path, which allows you to minimize redundancy among templates. In your Django settings, you specify a list of directories to check for templates with DIRS. If a template doesn’t exist in the first directory, it checks the second, and so on.
Let’s say the news/year_archive.html template was found. Here’s what that might look like:
Variables are surrounded by double-curly braces. {{ article.headline }} means “Output the value of the article’s headline attribute.” But dots aren’t used only for attribute lookup. They also can do dictionary-key lookup, index lookup and function calls.
Note {{ article.pub_date|date:"F j, Y" }} uses a Unix-style “pipe” (the “|” character). This is called a template filter, and it’s a way to filter the value of a variable. In this case, the date filter formats a Python datetime object in the given format (as found in PHP’s date function).
You can chain together as many filters as you’d like. You can write custom template filters. You can write custom template tags, which run custom Python code behind the scenes.
Finally, Django uses the concept of “template inheritance”. That’s what the {% extends "base.html" %} does. It means “First load the template called ‘base’, which has defined a bunch of blocks, and fill the blocks with the following blocks.” In short, that lets you dramatically cut down on redundancy in templates: each template has to define only what’s unique to that template.
Here’s what the “base.html” template, including the use of static files, might look like:
Simplistically, it defines the look-and-feel of the site (with the site’s logo), and provides “holes” for child templates to fill. This makes a site redesign as easy as changing a single file – the base template.
It also lets you create multiple versions of a site, with different base templates, while reusing child templates. Django’s creators have used this technique to create strikingly different mobile versions of sites – simply by creating a new base template.
Note that you don’t have to use Django’s template system if you prefer another system. While Django’s template system is particularly well-integrated with Django’s model layer, nothing forces you to use it. For that matter, you don’t have to use Django’s database API, either. You can use another database abstraction layer, you can read XML files, you can read files off disk, or anything you want. Each piece of Django – models, views, templates – is decoupled from the next.
This is just the surface
This has been only a quick overview of Django’s functionality. Some more useful features:
A caching framework that integrates with memcached or other backends.
A syndication framework that makes creating RSS and Atom feeds as easy as writing a small Python class.
More sexy automatically-generated admin features – this overview barely scratched the surface.
The next obvious steps are for you to download Django, read the tutorial and join the community. Thanks for your interest!

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzODYwMzg3MjQsNDk3ODE4ODEwXX0=
-->