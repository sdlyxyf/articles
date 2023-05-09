class list(object):
	    """
	    Built-in mutable sequence.    
	    If no argument is given, the constructor creates a new empty list.
	    The argument must be an iterable if specified.
	    """
	    def  append(self, *args, **kwargs): # real signature unknown
		        """ Append object to the end of the list. """
		        pass

    def clear(self, *args, **kwargs): # real signature unknown
        """ Remove all items from list. """
        pass

    def copy(self, *args, **kwargs): # real signature unknown
        """ Return a shallow copy of the list. """
        pass

    def count(self, *args, **kwargs): # real signature unknown
        """ Return number of occurrences of value. """
        pass

    def extend(self, *args, **kwargs): # real signature unknown
        """ Extend list by appending elements from the iterable. """
        pass

    def index(self, *args, **kwargs): # real signature unknown
        """
        Return first index of value.        
        Raises ValueError if the value is not present.
        """
        pass

    def insert(self, *args, **kwargs): # real signature unknown
        """ Insert object before index. """
        pass

    def pop(self, *args, **kwargs): # real signature unknown
        """
        Remove and return item at index (default last).        
        Raises IndexError if list is empty or index is out of range.
        """
        pass

    def remove(self, *args, **kwargs): # real signature unknown
        """
        Remove first occurrence of value.        
        Raises ValueError if the value is not present.
        """
        pass

    def reverse(self, *args, **kwargs): # real signature unknown
        """ Reverse *IN PLACE*. """
        pass

    def sort(self, *args, **kwargs): # real signature unknown
        """
        Sort the list in ascending order and return None.        
        The sort is in-place (i.e. the list itself is modified) and stable (i.e. the
        order of two equal elements is maintained).        
        If a key function is given, apply it once to each list item and sort them,
        ascending or descending, according to their function values.        
        The reverse flag can be set to sort in descending order.
        """
        pass

class dict(object):
    """
    dict() -> new empty dictionary
    dict(mapping) -> new dictionary initialized from a mapping object's
        (key, value) pairs
    dict(iterable) -> new dictionary initialized as if via:
        d = {}
        for k, v in iterable:
            d[k] = v
    dict(**kwargs) -> new dictionary initialized with the name=value pairs
        in the keyword argument list.  For example:  dict(one=1, two=2)
    """
    def clear(self): # real signature unknown; restored from __doc__
        """ D.clear() -> None.  Remove all items from D. """
        pass

    def copy(self): # real signature unknown; restored from __doc__
        """ D.copy() -> a shallow copy of D """
        pass

    @staticmethod # known case
    def fromkeys(*args, **kwargs): # real signature unknown
        """ Create a new dictionary with keys from iterable and values set to value. """
        pass

    def get(self, *args, **kwargs): # real signature unknown
        """ Return the value for key if key is in the dictionary, else default. """
        pass

    def items(self): # real signature unknown; restored from __doc__
        """ D.items() -> a set-like object providing a view on D's items """
        pass

    def keys(self): # real signature unknown; restored from __doc__
        """ D.keys() -> a set-like object providing a view on D's keys """
        pass

    def pop(self, k, d=None): # real signature unknown; restored from __doc__
        """
        D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
        If key is not found, d is returned if given, otherwise KeyError is raised
        """
        pass

    def popitem(self, *args, **kwargs): # real signature unknown
        """
        Remove and return a (key, value) pair as a 2-tuple.
        
        Pairs are returned in LIFO (last-in, first-out) order.
        Raises KeyError if the dict is empty.
        """
        pass

    def setdefault(self, *args, **kwargs): # real signature unknown
        """
        Insert key with a value of default if key is not in the dictionary.
        
        Return the value for key if key is in the dictionary, else default.
        """
        pass

    def update(self, E=None, **F): # known special case of dict.update
        """
        D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
        If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
        If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
        In either case, this is followed by: for k in F:  D[k] = F[k]
        """
        pass

    def values(self): # real signature unknown; restored from __doc__
        """ D.values() -> an object providing a view on D's values """
        pass


class tuple(object):
    """
    Built-in immutable sequence.
    
    If no argument is given, the constructor returns an empty tuple.
    If iterable is specified the tuple is initialized from iterable's items.
    
    If the argument is a tuple, the return value is the same object.
    """
    def count(self, *args, **kwargs): # real signature unknown
        """ Return number of occurrences of value. """
        pass

    def index(self, *args, **kwargs): # real signature unknown
        """
        Return first index of value.
        
        Raises ValueError if the value is not present.
        """
        pass


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzk5ODU1MzRdfQ==
-->