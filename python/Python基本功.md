相关的语法之类的解释我就不多做笔记，毕竟对于这些东西都已经烂熟于心，这里我就只做一些用法以及项目开发当中常要用到的一些关于Python基本功的笔记。
# 目录
  * [面向对象](#面向对象)
    * [下划线的应用](#下滑线的应用)
    * [面向对象的三大特性](#面向对象的三大特性)
      * [继承Extend](#继承Extend)
      * [封装和私有化Package](#封装和私有化Package)
      * [多态Polymorphism](#多态Polymorphism)
    * [形参之 *args 和 **kwargs](#形参之 *args 和 **kwargs)
  * [容器异常高阶函数内置函数](*容器异常高阶函数内置函数) 

#面向对象
  
## 面向对象的三大特性

### 继承Extend

 ```python
  class Animal：
    pass

  class Dog(Animal):
    pass

  class Cat(Animal):
    pass

 ```

### 封装和私有化Package

## 多态Polymorphism
  
  例如著名的 repr() 函数，它能够针对输入的任何对象返回一个字符串。这就是多态的代表之一。
  
  ```python
    repr([1,2,3])
    输出: '[1,2,3]'
  ```
  我们再来看看用OOP的思想实现的多态

  ```python

    class Animal:
        def __init__(self, name=""):
            self.name = name

        def talk(self):
            pass

    class Cat(Animal):
        def talk(self):
            print "Meow!"

    class Dog(Animal):
        def talk(self):
            print "Woof!"

    a = Animal()
    a.talk()

    c = Cat("Missy")
    c.talk()

    d = Dog("Rocky")
    d.talk()

  ```

## 下划线的应用

  "单下划线" 开始的成员变量叫做保护变量，意思是只有类对象和子类对象自己能访问到这些变量；
  "双下划线" 开始的是私有成员，意思是只有类对象自己能访问，连子类对象也不能访问到这个数据。
  
  * _xxx  不能用'from module import *'导入
    
    以单下划线开头（_foo）的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用“from xxx import *”而导入；
  
  * __xxx__ 系统定义名字
    
    以双下划线开头和结尾的（__foo__）代表python里特殊方法专用的标识，如 __init__（）代表类的构造函数。
  
  * __xxx 类中的私有变量名
    
    以双下划线开头的（__foo）代表类的私有成员；

  应该尽量避免用下划线作为变量名的开始。

  > 因为下划线对解释器有特殊的意义，而且是内建标识符所使用的符号，我们建议程序员避免用下划线作为变量名的开始。一般来讲，变量名_xxx被看作是“私有的”，在模块或类外不可以使用。当变量是私有的时候，用_xxx来表示变量是很好的习惯。因为变量名__xxx__对Python里特殊方法专用的标识，如 __init__（）代表类的构造函数。>
  

  
## 形参之 *args 和 **kwargs

  * *args 与 **kwargs

    *args* 接收的是一个元组对象， **kwargs 传递的是一个字典对象

    ```python

    def fun(*args **kwargs){

      print args, 'args_type = %s' % type(args)      #打印出来的类型是一个元组对象
      print kwargs, 'kwargs_type = %s' % type(kwargs) #打印出来的类型是一个字典对象

    }

    ```  



#容器异常高阶函数内置函数

## 容器

  * 列表 list  []
      
    ```python
      list_null = []
      list_int = [1,2,3,4,5,6,7,8,9]
      list_str = ['一', '二', '三', '四', '五', '六']
      list_bol = [True, False, True, Flase]
    ```

    * 添加 append(添加的值) 

      在列表的末尾添加参数

      ```python
        list_int.append(10)
      ```
    
    * 插入 insert(下标位置， 参数的值)

      在指定的位置插入参数

      ```python
        list_int.insert(10, 100)
      ```
    
    * 查看下标的长度 len(要查看的列表)

      ```python
        len(list_int)
      ```

    * 删除 pop(下标)

      ```python
        list_int.pop(10)
      ```

  * 字典 dict  {}
  
    ```python

      dict_null = {}
      dict_int = {1:1, 2:2, 3,3}
      dict_str = {'a':'aaa', 'b':'ccc', 'c':111, 'd':222}

    ```

    *  

  * 元组 tuple ()

    元组内的参数是不可变的

    ```python
      tuple_int = (1,2,3,4,5,6)
      tuple_str = ('a', 'b', 'c', 'd')
    ```



  * set 




## 迭代器(Iterable)

 ```python

   # 姿势1
   for i in range(10):
     print i

   # 姿势1.1
   [i for i in range(10)]

   # 姿势1.2
   [i for i in range if i/2 else i+1]

   # 姿势2
   i = 0
   while i < 10:
     i += i
     print i 


 ```


## 生成器 yied (Generator)

  ```python

  
  ```
  
## 装饰器(Decorator)

  ```python
  
  ```
  
## 异常处理(Exception)
  
  * try except finally
  
    ```python
      try:
        f = x, y: x+y
        f('hello', 123)
      except TypeExceptionError e:
        print e
      finally:
        print '不管是否捕获到异常，我依然执行！'
  
    ```
  * rain()

    ```python

    ```


## 匿名函数 (lambda)
  
  ```python

    func = lambda x, y: x+y

  ```

## 切片

## 排序 (Sort)

