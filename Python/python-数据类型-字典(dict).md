# Python3 数据类型-字典(dict)

字典(Dict)是另一种可变容器模型，且可存储任意类型对象。

## 字典的键值对应

字典的每个键值(key=>value)对用冒号`:`分割，每个对之间用逗号,分割，整个字典包括在花括号`{}`中 

格式：`d = {key1 : value1, key2 : value2 }`

键必须是唯一的，但值则不必。

值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。

#### 练习：创建字典

dict1 = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}


```
dict1{'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
```

也可如此创建字典：

dict1 = { 'abc': 456 }
dict2 = { 'abc': 123, 98.6: 37 }
print(dict1)
print(dict2)

```
{'abc': 456}
{'abc': 123, 98.6: 37}
```

## 访问字典内对象

#### 练习：访问字典内对象

把相应的键放入到方括号中。

dict = {'Name': 'Python', 'Age': 30, 'Class': 'First'}

print("dict['Name']: ", dict['Name'])
print("dict['Age']: ", dict['Age'])

```
dict['Name']:  Python
dict['Age']:  30
```

如果用字典里没有的键访问数据，会输出错误如下：

print("dict['Alice']: ", dict['Alice'])#KeyError: 'Alice'

```
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-10-7f558fa7afaf> in <module>
----> 1 print("dict['Alice']: ", dict['Alice'])#KeyError: 'Alice'

KeyError: 'Alice'
```

## 修改字典内对象

向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例:

#### 练习：修改字典内对象

dict1 = {'Name': 'Python', 'Age': 30, 'Class': 'First'}

del dict1['Name'] # 删除键 'Name'

print("dict['Age']:", dict1['Age'])
print("dict['Name']:", dict1['Name'])#KeyError: 'Name'

dict1.clear()     # 清空字典
del dict1         # 删除字典

```
dict['Age']: 30
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-2-1958e093e5cf> in <module>
      4 
      5 print("dict['Age']:", dict1['Age'])
----> 6 print("dict['Name']:", dict1['Name'])#KeyError: 'Name'
      7 
      8 dict1.clear()     # 清空字典

KeyError: 'Name'
```

## 删除字典内对象

能删单一的元素也能清空字典，清空只需一项操作。显示删除一个字典用`del`命令。

#### 练习：删除字典内对象

dict1 = {'Name': 'Python', 'Age': 7, 'Class': 'First'}

del dict1['Name'] # 删除键 'Name'

print("dict1['Age']: ", dict1['Age'])#Age键存在
print("dict1['Name']: ", dict1['Name'])#Name键已经删除，该行会报错

```
dict1['Age']:  7
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-11-7eca4184d0cf> in <module>
      4 
      5 print("dict1['Age']: ", dict1['Age'])#Age键存在
----> 6 print("dict1['Name']: ", dict1['Name'])#Name键已经删除，该行会报错

KeyError: 'Name'
```

但这会引发一个异常，因为用执行`del`操作后字典不再存在。

### 字典键的特性

#### 练习:字典键的使用

字典值可以是任何的 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。

两个重要的点需要记住：

1）不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住，如下实例：

dict2 = {'Name': 'Python1', 'Age': 7, 'Name': 'Python2'}

print("dict2['Name']: ", dict2['Name'])

```
dict2['Name']:  Python2
```

2) 键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行，如下实例：

dict3 = {['Name']: 'Python', 'Age': 7}

print("dict3['Name']: ", dict3['Name'])

```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-5-9ae26baf16c4> in <module>
----> 1 dict3 = {['Name']: 'Python', 'Age': 7}
      2 
      3 print("dict3['Name']: ", dict3['Name'])

TypeError: unhashable type: 'list'
```

## 字典内置函数&方法

Python字典包含了以下内置函数：

| 序号 | 函数及描述                                                   | 实例                                                         |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | `len(dict)`计算字典元素个数，即键的总数。                    | `dict = {'Name': 'Python', 'Age': 22, 'Class': 'First'};len(dict)` |
| 2    | `str(dict)`输出字典，以可打印的字符串表示。                  | `dict = {'Name': 'Python', 'Age': 22, 'Class': 'First'} ;str(dict)` |
| 3    | `type(variable)`返回输入的变量类型，如果变量是字典就返回字典类型。 | `type({})`                                                   |

## Python字典包含了以下内置方法：

help({})

```
Help on dict object:

class dict(object)
 |  dict() -> new empty dictionary
 |  dict(mapping) -> new dictionary initialized from a mapping object's
 |      (key, value) pairs
 |  dict(iterable) -> new dictionary initialized as if via:
 |      d = {}
 |      for k, v in iterable:
 |          d[k] = v
 |  dict(**kwargs) -> new dictionary initialized with the name=value pairs
 |      in the keyword argument list.  For example:  dict(one=1, two=2)
 |  
 |  Methods defined here:
 |  
 |  __contains__(self, key, /)
 |      True if D has a key k, else False.
 |  
 |  __delitem__(self, key, /)
 |      Delete self[key].
 |  
 |  __eq__(self, value, /)
 |      Return self==value.
 |  
 |  __ge__(self, value, /)
 |      Return self>=value.
 |  
 |  __getattribute__(self, name, /)
 |      Return getattr(self, name).
 |  
 |  __getitem__(...)
 |      x.__getitem__(y) <==> x[y]
 |  
 |  __gt__(self, value, /)
 |      Return self>value.
 |  
 |  __init__(self, /, *args, **kwargs)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  __iter__(self, /)
 |      Implement iter(self).
 |  
 |  __le__(self, value, /)
 |      Return self<=value.
 |  
 |  __len__(self, /)
 |      Return len(self).
 |  
 |  __lt__(self, value, /)
 |      Return self<value.
 |  
 |  __ne__(self, value, /)
 |      Return self!=value.
 |  
 |  __new__(*args, **kwargs) from builtins.type
 |      Create and return a new object.  See help(type) for accurate signature.
 |  
 |  __repr__(self, /)
 |      Return repr(self).
 |  
 |  __setitem__(self, key, value, /)
 |      Set self[key] to value.
 |  
 |  __sizeof__(...)
 |      D.__sizeof__() -> size of D in memory, in bytes
 |  
 |  clear(...)
 |      D.clear() -> None.  Remove all items from D.
 |  
 |  copy(...)
 |      D.copy() -> a shallow copy of D
 |  
 |  fromkeys(iterable, value=None, /) from builtins.type
 |      Returns a new dict with keys from iterable and values equal to value.
 |  
 |  get(...)
 |      D.get(k[,d]) -> D[k] if k in D, else d.  d defaults to None.
 |  
 |  items(...)
 |      D.items() -> a set-like object providing a view on D's items
 |  
 |  keys(...)
 |      D.keys() -> a set-like object providing a view on D's keys
 |  
 |  pop(...)
 |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
 |      If key is not found, d is returned if given, otherwise KeyError is raised
 |  
 |  popitem(...)
 |      D.popitem() -> (k, v), remove and return some (key, value) pair as a
 |      2-tuple; but raise KeyError if D is empty.
 |  
 |  setdefault(...)
 |      D.setdefault(k[,d]) -> D.get(k,d), also set D[k]=d if k not in D
 |  
 |  update(...)
 |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
 |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
 |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
 |      In either case, this is followed by: for k in F:  D[k] = F[k]
 |  
 |  values(...)
 |      D.values() -> an object providing a view on D's values
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
 |  __hash__ = None
```