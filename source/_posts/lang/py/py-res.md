title: "Python Resources"
date: 2015-03-01 16:46:12
tags:
- resource
categories:
- languages
- python

---
# Python

## Portal:
	- [pypi](https://pypi.python.org/pypi)

## Blog:
	- http://simple-is-better.com/
	- http://www.xlaobing.com/
	- http://www.liaoxuefeng.com/
	- [Practical Business Python](http://pbpython.com/)

# Project:
	- Trac
	- https://www.reviewboard.org/

# Read

- [cookbook](http://python3-cookbook.readthedocs.org/zh_CN/latest/)
- - [Learning Python](http://book.douban.com/subject/6049132/)
- [Python基础教程](http://book.douban.com/subject/4866934/)
- [Python学习手册(第4版)]
- [Python标准库]
- Learning Python(4th)
- Python Cookbook(2th)
- Beginning Python: From Novice to Professional Python基础教程（2th）
- Django Web 开发指南
- http://docs.python-guide.org/en/latest/
http://learnpythonthehardway.org/book/
http://ipython-books.github.io/cookbook/
https://github.com/ipython-books

## Tool:

- http://www.pydev.org

## Queue

- http://www.celeryproject.org

## Tornado:

- http://stackoverflow.com/questions/8086885/is-there-a-way-to-deploy-new-code-with-tornado-python-without-restarting-the-ser
- http://mirrors.segmentfault.com/itt2zh/index.html



# 知识点汇总

## 社区
- [Django-Project](https://www.djangoproject.com/)
- [Django-China](django-china.cn)

## 手册
- [PyTab](http://docs.pythontab.com/)
- [Python Guide](http://docs.python-guide.org/en/latest/)
- [Scrapy Manual](http://scrapy-chs.readthedocs.org/zh_CN/latest/)
- [Realpython](https://realpython.com/)

## 文章
- http://www.reddit.com/r/Python/comments/1rs7ub/what_are_some_mustwatch_python_videos/
- http://tmp.devcharm.com/pages/python-modules-you-should-know
- http://rogueleaderr.com/post/65157477648/the-idiomatic-guide-to-deploying-django-in

## 爬虫
- scrapy
- pyspider.org

## 知识点
- 概念与原理:
    - 虚拟机: 当虚拟机开始运⾏行时，它通过初始化函数完成整个运⾏行环境设置：
        • 创建解释器和主线程状态对象，这是整个进程的根对象。
        • 初始化内置类型。数字、列表等类型都有专⻔门的缓存策略需要处理。
        • 创建 __builtin__ 模块，该模块持有所有内置类型和函数。
        • 创建 sys 模块，其中包含了 sys.path、modules 等重要的运⾏行期信息。
        • 初始化 import 机制。
        • 初始化内置 Exception。
        • 创建 __main__ 模块，准备运⾏行所需的名字空间。
        • 通过 site.py 将 site-packages 中的第三⽅方扩展库添加到搜索路径列表。
        • 执⾏行⼊入⼝口 py ⽂文件。执⾏行前会将 __main__.__dict__ 作为名字空间传递进去。
        • 程序执⾏行结束。
        • 执⾏行清理操作，包括调⽤用退出函数，GC 清理现场，释放所有模块等。
        • 终⽌止进程。

    - 内存管理: 为提升执⾏行性能，Python 在内存管理上做了⼤大量⼯工作。最直接的做法就是⽤用内存池来减少操作系统内存分配和回收操作，那些小于等于 256 字节对象，将直接从内存池中获取存储空间。根据需要，虚拟机每次从操作系统申请一块 256KB，取名为 arena 的大块内存。并按系统页大小，划分成多个 pool。每个 pool 继续分割成 n 个大小相同的block，这是内存池最小存储单位。14block 大小是 8 的倍数，也就是说存储 13 字节大小的对象，需要找 block 大小为 16 的 pool 获取空闲块。所有这些都用头信息和链表管理起来，以便快速查找空闲区域进行分配。大于 256 字节的对象，直接⽤用 malloc 在堆上分配内存。程序运⾏行中的绝⼤大多数对象都⼩小于这个阀值，因此内存池策略可有效提升性能。当所有 arena 的总容量超出限制 (64MB) 时，就不再请求新的 arena 内存。⽽而是如同 "大对象" 一样，直接在堆上为对象分配内存。另外，完全空闲的 arena 会被释放，其内存交还给操作系统。

    - namespace: Python 有多种名字空间，⽐比如称为 globals 的模块名字空间，称为 locals 的函数堆栈帧名字空间，还有 class、instance 名字空间。不同的名字空间决定了对象的作⽤用域和⽣生存周期。

    - 垃圾回收
        事实上，Python 拥有两套垃圾回收机制。除了引⽤用计数，还有个专⻔门处理循环引⽤用的 GC。通常我们提到垃圾回收时，都是指这个 "Reference Cycle Garbage Collection"。

    - 编译
        Python 实现了栈式虚拟机 (Stack-Based VM) 架构，通过与机器无关的字节码来实现跨平台执行能力。这种字节码指令集没有寄存器，完全以栈 (抽象层面) 进行指令运算。

    - 执行
        相比 .NET、JAVA 的 CodeDOM 和 Emit，Python 天生拥有无与伦比的动态执行优势。

- 数据类型:
    **数据结构很重要，这⼏几个内置类型并不⾜足以完成全部⼯工作。像 C、数据结构、常⽤用算法这类基础是每个程序开发⼈人员都应该掌握的。**
    • 空值: None
    • 数字: bool, int, long, float, complex
        当超出 int 限制时， 会⾃自动转换成 long。 作为变⻓长对象，只要有内存⾜足够，⾜足以存储⽆无法想象的天⽂文数字。
        >>> Decimal('2.675').quantize(Decimal('.01'), ROUND_UP)! ! # 精确控制 round
Decimal('2.68')
        与字符串相关的问题总是很多，⽐比如池化 (intern)、编码 (encode) 等。字符串是不可变类型，保存字符序列或⼆二进制数据。

    • 序列: str, unicode, list, tuple
        从功能上看，列表 (list) 类似 Vector，⽽而⾮非数组或链表。
            • 列表对象和存储元素指针的数组是分开的两块内存，后者在堆上分配。
            • 虚拟机会保留 80 个列表复⽤用对象，但其元素指针数组会被释放。
            • 列表会动态调整指针数组⼤大⼩小，预分配内存多于实际元素数量。
        元组 (tuple) 看上去像列表的只读版本，但在底层实现上有很多不同之处。
            • 只读对象，元组和元素指针数组内存是⼀一次性连续分配的。
            • 虚拟机缓存 n 个元素数量⼩小于 20 的元组复⽤用对象。
        在编码中，应该尽可能用元组代替列表。除内存复用更高效外，其只读特征更利于并行开发。
    • 字典: dict
        字典 (dict) 采用开放地址法的哈希表实现。
        • 自带元素容量为 8 的 smalltable，只有 "超出" 时才到堆上额外分配元素表内存。
        • 虚拟机缓存 80 个字典复用对象，但在堆上分配的元素表内存会被释放。
        • 按需动态调整容量。扩容或收缩操作都将重新分配内存，重新哈希。
        • 删除元素操作不会⽴立即收缩内存。
        要判断两个字典间的差异，使用视图是最简便的做法。视图会和字典同步变更。
        字典是哈希表，默认迭代是⽆无序的。如果希望按照元素添加顺序输出结果，可以用 OrderedDict。
    • 集合: set, frozenset
        集合 (set) 用来存储⽆无序不重复对象。所谓不重复对象，除了不是同⼀一对象外，还包括 "值" 不能相同。集合只能存储可哈希对象，一样有只读版本 frozenset。
        在内部实现上，集合和字典非常相似，除了 Entry 没有 value 字段。集合不是序列类型，不能像列表那样按序号访问，也不能做切片操作。
        集合和字典、列表最⼤大的不同除了元素不重复外，还⽀支持集合运算。

- 表达式: 句法, 复制, 表达式, 运算符, 类型转换, 常用函数
- 函数: 创建, 参数, 作用域, 闭包, 堆栈, 包装
- 迭代器: 迭代器, 生成器, 模式
- 模块: 模块对象, 搜索路径, 导入, 构建包
- 类:　名字空间, 字段, 属性, 方法, 继承, 重载
    类: 由于历史原因，Python 2.x 同时存在两种类模型，算是个不大不小的坑。面向对象思想的演变也在影响着语⾔言的进化，单根继承在 Python 中对应的是 New-Style Class，而非 Classic Class。Python 3 终于甩掉包袱，仅保留 New-Style Class。所以呢，就算还在用 2.x 开发，也别再折腾
Classic Class，踏踏实实从 object 继承，或在源文件设置默认元类。
    抽象类: Abstract Class 无法实例化，且派⽣生类必须 "完整" 实现所有抽象成员才可创建实例。如果派⽣生类也是抽象类型，那么可以部分实现或完全不实现基类抽象成员。
    开放类: Open Class 几乎是所有动态语⾔言的标配，也是精华所在。即便是运行期，我们也可以随意改动对象，增加或删除成员。
    __slots__: 属性会阻止虚拟机创建实例 __dict__，仅为名单中的指定成员分配内存空间。这有助于
减少内存占⽤用，提升执⾏行性能，尤其是在需要⼤大量此类对象的时候。
    继承: super(), __base__, __bases__, __slots__
    操作符重载: __setitem__, __call__, __dir__, __getattr__, __cmp__

- 异常: 异常, 断言, 上下文
    异常不仅仅是错误，还是一种正常的跳转逻辑。如果你从没抛出过自定义异常，那么得好好想想了……
    断言 (assert) 虽然简单，但远比用 print 输出调试好得多。
    上下文管理协议 (Context Management Protocol) 为代码块提供了包含初始化和清理操作的安全
上下文环境。即便代码块发生异常，清理操作也会被执行。
        • __enter__: 初始化环境，返回上下⽂文对象。
        • __exit__: 执⾏行清理操作。返回 True 时，将阻⽌止异常向外传递。
    标准库 contextlib 提供了一个 contextmanager 装饰器，用来简化上下文类型开发。
    上下文管理协议的用途很广，比如：
        • Synchronized: 为代码块提供 lock/unlock 线程同步。
        • DBContext: 为代码块中的逻辑提供共享的数据库连接，并负责关闭连接。
        • 等等……

- 装饰器, 描述符, 元类
    装饰器 (Decorator) 在 Python 编程中极为常见，可轻松实现 Metadata、Proxy、 AOP 等模式。简单点说，装饰器通过返回包装对象实现间接调用，以此来插⼊入额外逻辑。
    想想看装饰器都能干嘛？
        • AOP: ⾝身份验证、参数检查、异常⽇日志等等。
        • Proxy: 对⺫⽬目标函数注⼊入权限管理等。
        • Context: 提供函数级别的上下⽂文环境，⽐比如 Synchronized(func) 同步。
        • Caching: 先检查缓存是否过期，然后再决定是否调⽤用⺫⽬目标函数。
        • Metaprogramming: 这个⾃自不必多说了。
        • 等等……
    描述符:
        很少有人会去刻意关注描述符 (Descriptor)，尽管它时时刻刻以属性、⽅方法的⾝身份出现。
            描述符协议：
            __get__(self, instance, owner) --> return value
            __set__(self, instance, value)
            __delete__(self, instance)
        描述符对象以类型 (owner class) 成员的⽅方式出现，且最少要实现⼀一个协议方法。最常见的描述符有 property、staticmethod、classsmethod。访问描述符类型成员时，解释器会自动调用与行为相对应的协议方法。
            • 实现 __get__ 和 __set__ 方法，称为 data descriptor。
            • 仅有 __get__ 方法的，称为 non-data descriptor。
            • __get__ 对 owner_class、owner_instance 访问有效。
            • __set__、__delete__ 仅对 owner_instance 访问有效。

        元类
        类型对象地位超然，负责创建对象实例，控制对象⾏行为 (⽅方法)。那么类型对象⼜又由谁来创建呢？—— 元类 (metaclass)，也就是类型的类型。

## 标准库
- 字符串:
    re:
        • match(): 匹配字符串开始位置。
        • search(): 扫描字符串，找到第⼀一个位置。
        • findall(): 找到全部匹配，以列表返回。
        • finditer(): 找到全部匹配，以迭代器返回。
    MatchObject:
        match、search、finditer 返回的对象 —— MatchObject。
        • group(): 返回匹配的完整字符串。
        • start(): 匹配的开始位置。
        • end(): 匹配的结束位置。
        • span(): 包含起始、结束位置的元组。
        • groups(): 返回分组信息。
        • groupdict(): 返回命名分组信息。
    StringIO
        提供类⽂文件接⼝口的字符串缓冲区，可选⽤用性能更好的 cStringIO 版本。

## 数据存储
- serialization
    marshal: Python 专⽤用的序列化算法，PyCodeObject 就是⽤用该算法序列化后保存到 pyc ⼆二进制⽂文件。与具体的机器架构⽆无关，但可能随 Python 版本发⽣生变化。通常不建议⽤用来存储⾃自定义数据。支持：None, bool, int, long, float, complex, str, unicode, tuple, list, set, frozenset, dict,code objects, StopIteration。容器元素必须是所⽀支持类型，不能是递归引⽤用。
    pickle: 应该⽤用 cPickle 代替 pickle，按官⽅方⽂文档的说法有千倍的提升，且可相互替换。支持⽤用户⾃自定义类型，⽀支持三种协议版本：
    • 0: 使⽤用可显⽰示的 ASCII 字符编码，便于阅读和⼿手⼯工编辑。(默认)
    • 1: 兼容早期 Python 版本的⼆二进制格式。
    • 2: 最有效的⼆二进制编码格式。

## 门户
- djangoproject: [https://www.djangoproject.com/](https://www.djangoproject.com/)

## 工具
- 爬虫： [http://scrapy.org/](http://scrapy.org/)
- 数据可视化: [http://gephi.github.io/](http://gephi.github.io/)

## 文章
  * [PEP8 Style Guide for Python Code](PEP8 Style Guide for Python Code): Python编程标准
  * [PEP7 PEP8 Style Guide for Python Code](PEP8 Style Guide for Python Code): Python C 扩展
  * [Code Like a Pythonista: Idiomatic Python](http://python.net/~goodger/projects/pycon/2007/idiomatic/handout.html): Python 编程技巧
  * [PEP318 Decorators for Functions and Methods](http://www.python.org/dev/peps/pep-0318/) Decorators使用
  * [Python regular expression documentation](http://docs.python.org/2/library/re.html) Python 正则表达式
  * [Python Web Server Gateway Interface v1.0](Python Web Server Gateway Interface v1.0) Python Web Guide
  * [How To Use Linux epoll with Python](http://scotdoyle.com/python-epoll-howto.html) Python Epoll
  * [Google Python Style Guide](https://google-styleguide.googlecode.com/svn/trunk/pyguide.html) Google Python Guide
  * [Python best practices](http://www.fantascienza.net/leonardo/ar/python_best_practices.html) Python 最佳实践
  * [Python Types and Objects](http://www.cafepy.com/article/python_types_and_objects/) Python 类型和对象,[中文版](http://wiki.woodpecker.org.cn/moin/PyTypesAndObjects)
  * [Python Attributes and Methods](http://www.cafepy.com/article/python_attributes_and_methods/python_attributes_and_methods.html) Python 属性与方法
  * [Coroutines via Enhanced Generators](Coroutines via Enhanced Generators)
  * [Python Tips, Tricks, and Hacks ](http://www.siafoo.net/article/52)
  * [PEP20 Examples](http://artifex.org/~hblanks/talks/2011/pep20_by_example.py.txt)
  * [Hiden features of Python](http://stackoverflow.com/questions/101268/hidden-features-of-python)很少被了解但很有用的特性。

## Books
  * [Python 基础教程](http://book.douban.com/subject/4866934/) 很基础，说的也很明白，适合入门
  * [Python 参考手册](http://book.douban.com/subject/5401851/) 工具书，对常用的工具，模块做介绍
  * [Python 源码剖析](http://book.douban.com/subject/3117898/) 代码分析的很精彩，提升内功
  * [Python 高级编程](http://book.douban.com/subject/4212921/) 高级技巧

## 列表高级操作
## filter
过滤器，调用一个bool函数来迭代遍历每个seq中的元素，返回一个bool_seq返回值为true的元素序列。

    {% highlight python %}
        b = filter(lambda x:x>5,xrange(0,10))
        #当filter 参数为None，会调用identity()函数，list中
        #为假的元素将被过滤
        b = filter(None,xrange(0,10)) {% endhighlight %}

## map

map的第一个参数作用与给定序列的每一个元素，并用一个list做为返回值。

    {% highlight python %}
        b = map(lambda x:x+10,xrange(1,10)) {% endhighlight %}

## reduce

reduce的第一个参数func为一个二元参数；func将作用于seq的每一个元素，
**每次携带一对（previous result 和current value）,连续的将现有结果和下一个值func预算，作用于随后的结果上**，
最后归约成一个值进行返回。

    {% highlight python %}
        b = reduce(lambda x,y:x+y,xrange(1,10))
        #求阶乘
        f = lambda N:reduce(lambda x,y:x*y, xrange(1,N+1))
        print f(5) {% endhighlight %}

## list comprehensions(列表推导式)

举例:

    {% highlight python %}
        l = [i for i in range(10) if i % 2 == 0] {% endhighlight %}

优点：
  * 不需要使用计数器
  * 不要重复确定列表的某个元素要进行使用，省去索引过程，更加高效
  * Python对其进行特殊的优化，执行效率非常高

## enumerate(简洁索引)

举例：

    {% highlight python %}
        # 注意并没有声明 i 为0和对其进行迭代累加
        seq = ["one", "two", "three"]
        for i, element  in enumerate(seq):
            seq = '%d: %s' % (i, element)
    {% endhighlight %}

# lambda表达式

匿名函数，lambda中的所有指针全部失效，python解释器将不再创建属于该函数的stack区间
保留临时变量，注意这与函数的压栈截然不同。实际上lambda完全是一个表达式，与C中
macro类似。可以将lambda赋予外部变量或指针，可以接受参数，也可以用于传递返回结果。

一些例子：

    {% highlight python %}
        true = lambda :True
        false = lambda :False
        sqrt = lambda x:x**0.5 {% endhighlight %}

资源参考，[这里](http://www.secnetix.de/olli/Python/lambda_functions.hawk)

## def 与 lambda 区别

  * def 是语句
  * lambda 是表达式

# closure 闭包

在GUI和DB事务设计中，闭包被广为使用，用来限制变量的越权读写。
闭包函数可以自由的操作上层函数的变量，最高至global域。反之，上层函数
无法操作闭包内的变量 ，因为闭包是在上层函数创建之后产生的。
当内外冲突时，closure将忽略上层变量保留内部变量。

代码参考,[这里](https://github.com/tianweidut/CookBook/blob/master/python/closuree.py)


# 格式化字符串

## %s, %r 区别

  * %s 表示对字符串进行str()操作，转化为str类型，创建了一个新的对象
  * %r 表示repr()操作，是object的字符串形式，并没有进行转化

    {% highlight python %}
        d = datetime.date.today()
        str(d) --> show like '2012-12-07'
        repr(r) --> only for string 'datetime.date(2012,12,7)'
        d = 'test'
        a = 'result:%s'%d --> result:test
        a = 'result:%r'%d --> result:'test' {% endhighlight %}

# Python Package

## __init__.py:
  * __init__.py 掌握这Python的包机制，控制包的导入行为
  * 当为空时，仅仅导入包，不做额外的操作。
  * 当不为空时，会在该包导入时执行相关内容。
     * __all__ : 将其列表中的子模块和子包导入到当前作用域中。可以突破文件系统限制。如果不定义__all__，无法实现all import。参见[这里](http://docs.python.org/2/tutorial/modules.html#importing-from-a-package)。
     使用时，代码如下
    {% highlight python  %}
        __all__ = ['pack1','module1','module2']
        # import all modules
        from testpack import *
    {% endhighlight %}

# 常见陷阱

## tuple陷阱

* 良好的写作方式是（item1,item2,）
* 当单个元素是若写成（item1）就各种错误，所以一定要（item1,）明确的告诉这是元组

------

# Design Pattern in Python

## Signleton

[__new__实现单例](http://www.cnblogs.com/lovemo1314/archive/2011/05/03/2034927.html)

[metaclass实现单例](http://code.activestate.com/recipes/102187-singleton-as-a-metaclass/)

[多种方法](http://my.oschina.net/u/140191/blog/51295)

# 异常与with

## with...as

替代try...finally语句，实现发生错误时候，清理资源，应用在一下场合：
* 关闭一个文件
* 释放一个锁
* 创建一个临时的代码补丁
* 在特殊环境中运行受保护的代码
简单的说就是能在**代码块的前和后调用一些代码**提供了方便。举例：

    {% highlight python %}
        with file('/etc/hosts') as hosts:
            for line in hosts:
                print line {% endhighlight %}

当类实现with协议，即实现__exit__和__enter__两个函数时，就可以使用with。
举例：

    {% highlight python %}
        Class Context(object):
            def __enter__(self):
                print "enter init"
            def __exit__(self, exception_type, exception_value,
                        exception_traceback):
                # 当发生错误时，在三个参数会被填充，默认为None。
                # 当with中抛出异常，context不应该再次抛出异常，应该进行处理。
                print "exit value"
                if exception_type is None:
                    print "None exception"
                else:
                    print "with an error  (%s) " % exception_value
        with Context() as c:
            print "out of the context"
            raise TypeError("here is a bug!")
    {% endhighlight %}

上段代码执行顺序如下：

1. 执行Context()表达式，返回Content Manager子类给c，Content Manager规定__enter__和__exit__。
2. 调用c的__enter__方法
3. 执行with中的内容
4. 如果with中代码抛出异常，执行c的__exit__函数，同时传递了异常的类型，值和调用堆栈。
5. 若with中未抛出异常，执行__exit__函数，不传递参数。

------

# unknow features

## __new__ 与 __init__

* new的优先级更高一些
* __new__ 一般用于继承内置类，返回的是一个对象，可以应用在单例模式中；相当与JAVA里面的构造器
* __init__ 只做初始化工作，没有返回值。
* 如果重写了__new__，而在__new__中没有调用__init__,则__init__将不起作用。
* 参考[这里](http://docs.python.org/reference/datamodel.html#object.__new__)，还有[这里](http://www.cnblogs.com/lovemo1314/archive/2011/05/03/2034927.html)

Python 程序的性能问题饱受诟病，按个人理解，首先要保证算法的复杂度在可以接受的范围，
这个也是影响性能的关键，其次当代码变得越来越长，模块越来越多，快速的得到性能指标数据，
分析瓶颈，并做出针对性的优化变得十分重要。

性能指标:
  - 运行速度：包括程序运行时间，各个函数调用用时，运行速度的瓶颈等
  - 内存：总体占用内存的多少，是否有内存泄露等

## 运行速度

### Linux Time Command
`time` 命令能够快速的掌握程序运行时间，

    {% highlight python %}
        time python hello.py
        real    0m1.028s
        user    0m0.001s
        sys     0m0.003s
    {% endhighlight %}

输入的含义：

  - real: 实际程序运行的用时，从开始到结束，包括等待其他进程的时间（如等待IO）
  - user: user mode，非kernel的cpu time spend，可以认为是该进程真正运行时间，排除其他干扰。
  - sys: ,kernel的cpu time spend

其中 `user+sys != real`, 很容易理解，程序执行分配的cpu时间片加上等待时间才是真正程序运行，外界
看到的时间消耗。当`user+sys`比`real`小得多时，应该是系统load比较高或改程序io wait较多。

### Python code
可以写一个`Timer` Class，作为`context manager`，自己定义`__enter__`和`__exit__`，分别标记开始和结束，
是`with`或`decorator`来进行标记和计算。


### line profiler
[line profile](https://pythonhosted.org/line_profiler/), 是测试script每行执行情况的工具，使用的时候，
只需要对所需观察的函数添加`@profile`的`decorator`，并用`kernprof.py -l -v xxx.py`运行该程序，然后就会得到
每行的分析数据。

## 内存使用

### memory profiler
[memory profiler](https://github.com/fabianp/memory_profiler)，能够得到script每行的内存占用情况，使用时
对所需观察的函数添加`@profile`的`decorator`，并用`python -m memory_profiler xxx.py`运行该程序。

### objgraph memory leak
CPython的编译器实现使用引用计数的方式对object的内存进行管理，对象保存但计数为0，就会发送memory leak.
[objgraph](http://mg.pov.lt/objgraph/)，可以得到object的reference关系以及添加或删除的操作等，
使用的时候通过`pdb`来注入`objgraph`。

## Refer
- [Real, User and Sys process time statistics](http://stackoverflow.com/questions/556405/what-do-real-user-and-sys-mean-in-the-output-of-time1)
- [A guide to analyzing Python performance](http://www.huyng.com/posts/python-performance-analysis/)

1. class
    1. __x 私有变量， 私有变量和公共变量可以同名
    2. def __x(): 私有函数
    3. __x__  就不是私有变量，一般是类的方法
    4. 但是如果是对象实例化之后添加的__属性, 就不是私有变量，可以获取(应为该特性是在编译时发生的)

2. class
    1. class 和 self 并没有任何实际含义，只是通用命名
    2. self 只是一个占位符
3. '{2}-{0}-{1}'.format(2009, 4, 100)
4. 直接使用对象的bool 值
5. descriptor 数据描述符
    1. 对属性做一些额外的工作
    2. staticmethod 和 classmethod 区别
6. class 继承
    1. 菱形继承  -->  C3 算法
7. python 中任何函数都是有返回值的，及时没有写任何东西，默认会返回None
8. bugs:
    1. if a: --> 这个有时候没法判断到底是None，还是空list，还是Fasle，所以应该明确指定类型
    2. a = []; 如果 if a == []: 这个时可以进入if, 但是 if a is []: 这个就不会， if not a: 这个也可以进入判断
    3. is 与 == 的区别：
      1. is 是比较相同的对象实例
      2. == 完全看 `__eq__()` 函数的实现

9. isinstance 判断对象的类型
10. 三元表达式技巧
    1. a = b if conf else c
    2. a = b or c
11. 当发生异常是，打印异常堆栈信息：
    1. import traceback
    2. traceback.print_exc()
12. with 语句
    1. with 包裹的任何内容，如果发生异常，自动调用f.close() 来关闭文件
13. os.environ 反应系统环境变量，返回字典
14. SIGTERM 与 SIGKILL
    1. SIGTERM： 友好关闭新号，进程可以捕捉这个新号，根据需要来关闭进程，在关闭前可以执行默写清楚程序，包括完成正在执行的进程，关闭打开的文件等；同时进程是可以忽略这个新号的
    2. SIGKILL：进程不能忽略这个新号
15. '\r\n' 与 '\n': http://stackoverflow.com/questions/1761051/difference-between-n-and-r
16. 命名空间问题
    1. Python使用命名空间来实现对变量轨迹
    2. 名字空间实际上是一个dict类型
    3. 在一个 Python 程序中的任何一个地方，都存在几个可用的名字空间。每个函数都有着自已的名字空间，叫做局部名字空间，它记录了函数的变量，包括函数的参数和局部定义的变量。每个模块拥有它自已的名字空间，叫做全局名字空间，它记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。还有就是内置名字空间，任何模块均可访问它，它存放着内置的函数和异常。
    4. 查找顺序
      1. 局部名字空间――特指当前函数或类的方法。如果函数定义了一个局部变量 x，或一个参数 x，Python 将使用它，然后停止搜索。
      2. 全局名字空间――特指当前的模块。如果模块定义了一个名为 x 的变量，函数或类，Python 将使用它然后停止搜索。
      3. 内置名字空间――对每个模块都是全局的。作为最后的尝试，Python 将假设 x 是内置函数或变量。
    5. 如果 Python 在这些名字空间找不到 x，它将放弃查找并引发一个 NameError 异常，同时传递 There is no variable named 'x'
    6. 在运行时可以对名字空间进行访问，局部locals(), 全局globals(),返回的都是字典
    7. locals（）返回的实际上是局部变量字典的一个拷贝，也就是说如果locals()['x'] = 1 这是对locals()局部变量字典没有影响的，但globals()则可以改变
17. built-in 自省函数
    1. getattr 返回属性值, getattr(Instance, "attr", "default") 对对象Instance获取attr属性，如果有就返回该属性的值，如果没有就返回default. 可以用getattr实现工厂模式
    2. 使用技巧: a = ["a", "b"]; a.pop, a.pop() # 一个返回built-in对象，一个返回弹出的值；getattr(a,"pop")() 等价于弹出一个值； getattr(a, "append")("c") 添加一个值到末尾
18. __import__ 动态导入模块
    1. http://blog.donews.com/limodou/archive/2005/06/10/422024.aspx
19. print "aa|bb|cc|dd|ee|ff".split('|',1) 结果是['aa', '。。。'] 最多分割几次
20. getpass 可以在终端或tty中动态的获取输入密码，这个时subprocess.call做不到的
21. round(n, 2) 四舍五入保留两位小数
22. callable() 检测该对象是否可以调用，也就是说类实现了__call__， 但是调用可能会失败
23. import this
    1. beautiful is better than ugly
      1. 不要过多的嵌套使用map, filter
    2. explicit is better than implicit
      1. import 某个包的时候，一定禁止使用from xxx import *, 推荐的做法是能有多少个就写多少个
      2. 如: from corelib.consts import (K_SAYING, K_NOTE, K_PHOTO, K_TOPIC)
    3. simple is better than complex
      1. 尽可能简单的表达意图
      2. for i in resered(seq): foo(i);
      3. for i in seq[::-1]: foo(i)
    4. zip 对两个集合同时迭代
      1. for i,j in zip(seq1, seq2): print  i,j
    5. 多用列表推倒式，能使表达更加简洁
    6. flat is better than nested
      1. 用小函数进行分解，避免过多的if 嵌套关系
    7. sparse is better than dense
      1. 使用适当的空格、空行来使表达更加清晰
    8. 一些习惯
      1. if x != []: pass (bad); if not x: pass; (good)
      2. for i in range(len(seq)): print i, seq[i] (bad); for i, item in enumerate(seq): print i, item (good)
    9. Error should never pass silent!
      1. 对于异常，一定不能简单的pass；要么写logger，要不就raise
    10. 如果一个implementation很容易解释，那么这是一件好事
    11. KISS: keep it simple and stupid
    12.  多使用decorator, 这样能够简化表达，提取公共部分
    13. 对于一些使用后就废弃的变量和函数名，可以用_ 来表述
24. iterators
    1. 可以将序列转化成iter，调用next方法就调用输入一次，如果没有可以输出的了就会抛出StopIteration
    2. 但是在使用中没必要总是监控这个异常，可以像循环使用
    3. 一个iterator描述一个数据流，支持的next方法表达下一个读取的元素是什么
    4. 生成器是创建迭代器的简单方法，生成器运行到yield会被简单的挂起，程序运行状态暂停，下次调用next时恢复执行
    5. all 和 any 是对迭代器快速判断的一个方法
25. Class
    1. __new__ 与 __init__ : 对象创建的时候一定会调用__new__,无论__init__是否被调用
    2. __new__ 调用发生在 __init__ 调用前， __new__ 用来检查对象的初始化情况，或进行一些更底层的初始化工作
26.  简单地讲，yield 的作用就是把一个函数变成一个 generator，带有 yield 的函数不再是一个普通函数，Python 解释器会将其视为一个 generator，调用 fab(5) 不会执行 fab 函数，而是返回一个 iterable 对象！在 for 循环执行时，每次循环都会执行 fab 函数内部的代码，执行到 yield b 时，fab 函数就返回一个迭代值，下次迭代时，代码从 yield b 的下一条语句继续执行，而函数的本地变量看起来和上次中断执行前是完全一样的，于是函数继续执行，直到再次遇到 yield。
27. Popen 可以利用stdin, stdout使用PIPE的方式来控制输出和输入，实现对一个cmd应用的控制
28. 本地配置和线上配置，通过在config.py 底部写入try: from local_config import * except: pass 来覆盖config实现本地的切换
29. urlparse 可以用来解析网址
30. glob 用来进行文件查找，可以使用正则表达式
31. Python Generator
    1. iterating object , python 中可迭代类型，也就是可以for的object，包括list, tuple, set, dict, string, File
    2. Consume iterable object
      1. reduction:  sum(s), min(s), max(s)
      2. constructor: list(s), tuple(s), set(s), dict(s)
      3. in operator
    3. Iteration Protocol
      1. iter() --> 就让对象遵循iteration protocol 协议，能进行iteration操作
      2. next() 获取当前迭代对象，当迭代完成时，raise StopIteration 异常
      3. 让一个class符合iteration协议，需要实现__iter__() 和 next()方法，当进行for迭代时，不会抛出StopIteration异常，只有用next()方法结束迭代才会抛出StopIteration异常
    4. generator 产生a sequence of results 代替单一值，关键是使用yield
      1. generator 对象不会马上执行，只有调用next才开始执行，next的调用可以直接调用该函数，也可以用for的方式
      2. 调用该函数时，会在yield产生数值，然后函数suspend，保存状态，停止运行，直到下次再调用
      3. A generator is a one-time operation. You can iterate over the generated data once, but if you want to do it again, you have to call the generator function again.
      4. list comprehension 是 generator, 使用(i for i in range(10))(generator), 不是[i for i in range(10)](list)
      5. generator 一旦被消费就不能再使用
      6. 标准语法： (expression for i in s if cond1 for j in t if cond2 … if condfinal) --> for i in s: if cond1: for j in t: if condo:… if condfinal: yield expression
      7. generator 是可以连接起来，类似于pipeline的方式
      8. 优点：避免产生大的临时文件或list，尤其是处理大文件时
      9. 原理：base on the concept of pipelining data between different components
      10. os.walk 是一个generator
      11. 典型使用：
        1. Generate a sequence of TCP connections
        2. Generate IO events on a set of sockets
32. python uuid http://www.douban.com/note/69073375/
33. cPickle http://docs.python.org/2/library/pickle.html#module-cPickle
34. os.rmdirs 只能删除目录中为空的，如果要彻底阐述使用shutil.rmtree(path)
35. nose test python 的测试框架 http://nose.readthedocs.org/en/latest/
36. os.path.join 是不能路径进行实际转化的，如os.path.join(“../../“) -》显示的就是../../， 显示实际的应该使用os.path.abspath(‘../../‘)
37. try .. except … finally 结构中无论中间try中间发生什么，包括return，finally 都将会执行， 有时会造成潜在bug
38. a=[] a[0] 会产生错误；但可以用a[:1] 来进行，如果为空则返回[]
39. {} 形成字典 比 dict() 形成字典要更快速
40. python 的序列解包 unpacking
    1. a,(b,c),d=[1,(2,3),4]
    2. a, b = b, a swap
41. zip
    1. a = [1,2,3]  b=[a,b,c]  c = zip(a,b) —> c :[(1,a), (2,b), (3,c)]; —> zip(\*c) : [(1,2,3), (a,b,c)]
42. flat list
    1. a=[[1,2],[3,4],[5,6]] —> [j for i in a for j in i]
    2. list(itertools.chain.from_iterable(a))
43. set
    1. a = {1,2,3}  === a = set([1,2,3])
44. defaultdict collections.defaultdict
    1. collections.defaultdict(int), 即使字典中没有响应的元素，也可以获取值，默认为0 ，如 d[‘a'] : 0
    2. collections.defaultdict(str),
    3. collections.defaultdict(lambda : ‘[tttt]’)
    4. https://gist.github.com/hrldcpr/2012250
    5. tree = lambda: collections.defaultdict(tree); root = tree()  python的树结构
45. 集合相乘
    1. forpinitertools.product([1,2,3],[4,5])
    2. forpinitertools.product(\*([[0,1]]\*4)):  0000 —> 1111
46. python trick http://sahandsaba.com/thirty-python-language-features-and-tricks-you-may-not-know.html
47. 使用列表推导式的一个问题是，会将所有的数据都载入内存，为了避免这种情况，使用generator 进行改造，(x**2 for x in a_list if x > 0) ,应该经常在代码中使用生成器表达式.
48. 装饰器是一个包装了另一个函数的特殊函数：主函数被调用，并且其返回值将会被传给装饰器，接下来装饰器将返回一个包装了主函数的替代函数，程序的其他部分看到的将是这个包装函数.  @decorator 意味着分开执行了两部函数，如下：

    {% highlight python %}
    @timethis
    def run():
        pass
    # 等价于 run = timethis(run)
    {% endhighlight %}

49. 上下文管理: contextlib 上下文管理器和with声明相关的工具
    1. 上下文管理器，需要定义一个类具有`__enter__`和`__exit__`方法。上下文管理器会被with所激活，对with块的入口点和出口点进行相应得处理。`__enter__`进入的时候会返回一个在上下文使用的对象。`__exit__`常做资源清理使用，如`with open('f.txt') as f: pass`
    2. 同时存在`@contextmanager`,可以将一个类快速变成`context manager object`,如下：

        {% highlight python %}
        @contextmanager
        def demo(label):
            start = time.time()
            try:
                yield
            finally:
                end = time.time()
                print 'Finish the task, use %s' % (end-start)
        # 也就是将yield之前的作为__enter__, yield之后的作为__exit__。
        {% endhighlight %}

50. 描述器决定了对象属性是如何被访问的。描述器的作用是定制当你想引用一个属性时所发生的操作.`__get__`, `__set__`, `__del__` 三个操作
51. MetaClass: 提供一个改变Python类行为的有效方法。MetaClass定义的是一个类的类。`type`就是一个元类，而且是python中最常见的元类，因为它使python中所有类的默认元类。
52. http://coolshell.cn/articles/11265.html ，注意其中fib的cache，cache只会初始化一次，每个fib返回的都是wrapped，所以不用global变量
53. subprocess: 用来spawn新的进程，并connect该进程的input/output/error pipe，获得returncode.
  1. 替代：`os.system`, `os.spawn`, `os.popen`, `commands`, `popen2`
  2. subprocess.call 等待subprocess执行结束，返回状态码
  3. subprocess.check_calll 等待subprocess执行结束，返回状态码，当状态码非0时，抛出subprocess.CalledProcessError异常
  4. subprocess.check_output 与check_call类似，但返回的是subprocess的输出
  5. subprocess.CalledProcessError 在check_call和check_output返回非0状态码时，抛出该异常，有cmd, returncode, output三个参数可以使用
  6. subprocess.popen 提供更复杂的构造函数，poll/wait/communicate/send_signal/terminate/kill
  7. 常用的写法

        {% highlight python %}
        # old: replace shell
        output = 'mycmd myargs'
        # new
        output = check_output(['mycmd', 'myargs'])

        # replace shell pipeline
        # output = 'dmesg | grep data'
        p1 = check_output(['dmesg'], stdout=PIPE)
        p2 = check_output(['grep', 'data'], stdin=p1.stdout, stdout=PIPE)
        # p1调用close，需要在p2创建后，这样可以让p1在p2发生exit时，接受SIGPIPE信号
        p1.stdout.close()
        output = p2.communicate()[0] #communicate 返回(stdout, stderr)元组

        # 以上方式也可以用:
        output = check_output('dmesg | grep data', shell=True)

        # old: os.system
        status = os.system('mycmd myargs')
        # new: call
        status = subprocess.call('mycmd myargs', shell=True)
        {% endhighlight %}
54. multiprocess: 众所周知python的GIL机制，让thread在python中支持的并不好，使用多进程可以在一定程度上解决这个问题。multiprocess 提供一些列类似thread的接口，来
操作多进程。
  1. 支持两种进程间通信的方法：Queues(进程和线程安全的)和Pipes
  2. 支持进程间的同步，可以使用Lock
  3. 进程状态共享：实际上在并发编程中应该尽量减少状态的共享，使用Value和Array共享数据，同时他们是进程和线程安全的，还可以使用Manager()
  4. Pool提供进程池
  5. Process.join 用来block调用thread，直到该process发生terminated，一个进程可以被join多次；不能join self，会发生deadlock，也必须在start之后

基于Python的编程接口。
目前有几个主流的Python接口：

 * [Happy](https://code.google.com/p/happy/) 基于Jython的，原理是将Python代码转化为Java代码，不推荐使用，因为Jython严重限制了Python库的使用。
 * [Pydoop](http://pydoop.sourceforge.net/) 基于Cython实现，利用C语言底层的pipeline机制，可以使用Numpy之类的C语言库，而且能在C语言层面对HDFS进行操作，同时
  能够对MR compnents(RecordReader, RecordWriter, Patitioner)进行访问，最后还能访问Hadoop的配置文件，设置计数器等，看起来很不错。
 * [Hadoopy](http://www.hadoopy.com/en/latest/) 又一个基于Cython实现的Python编程接口，代码非常简练，文档也完善
 * [dumbo](https://github.com/klbostee/dumbo/wiki) 是纯Python实现的框架，利用Hadoop的Streamming机制，最后选择的也是这个框架，原因只有一点，足够Pythonic，让人爱不释手。
 * [Python native](http://www.michael-noll.com/tutorials/writing-an-hadoop-mapreduce-program-in-python/) 也可以用Python自己写STDIN和STDOUT来做，链接里的是一篇非常好的介绍。

总结一下在MapReduce编程和dumbo使用中遇到的一些问题和解决方法。

## 调试方法

  * stderr: 由于dumbo是利用python的标准输入和输出流与hadoop进行通讯，所以绝对不能使用print直接打印变量。可以使用sys.stderr向错误流中输出，
  这样在运行中就可以直接观察运行结果。
  实例：
    {% highlight python %}
        def debug(content,pos=None):
            print >> sys.stderr, "+"*15
            if pos is not None:print >> sys.stderr, pos
            print >> sys.stderr, content
            print >> sys.stderr, "-"*15 {% endhighlight %}

  * dumbo 调试变量：当使用Mapper和Reducer类时，除了可以方便的进行初始化外，还可以携带一些变量，监控执行过程，并且能在Hadoop WEB页面展示出来。
     * params: 一个字典结构，可以携带外部变量，用来传递一些变量，文件等。
     * counters: 可以视为一个defaultdict，包含dumbo.Counter objects。
     * status: 该字段可以将状态或调试信息展示在Hadoop的web interface。

  * remote debugger: 在dumbo中嵌入远程调试器，如Winpdb或Komodo IDE。参看[这里](https://groups.google.com/forum/?fromgroups=#!topic/dumbo-user/SLN3teTKgIU)，
  还有[这里](https://gist.github.com/866301)。

http://www.ibm.com/developerworks/cn/linux/l-cn-pythondebugger/index.html
http://magustest.com/blog/python/use-pdb-debug-python/
