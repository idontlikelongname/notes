## Python tutorials notebooks
### url: https://cycleuser.gitbooks.io/think-python/content/chapter14.html
#### 列表 list

#### 字典 dictonary

#### 元组 tuple

#### 文件操作
数据库 dbm 键和键值必须是字符串或者二进制，如果用其它类型数据，就错误了
pickle　可以把几乎所有类型的对象翻译成字符串模式，以便存储在数据库中，然后用的时候还可以把字符串再翻译回来


#### 管道
在shell下能够启动的所有程序，也都可以在Python中启动，这要用到一个pipe对象，一个pipe对象就代表了一个运行的程序



#### 模块
如果导入了一个已经导入过的模块，python是不会有任何提示的，python并不会重新读取模块文件，即使该文件又被修改过也是如此
所以如果想要重新加载一个模块，可以用内置函数reload，但这个也不靠谱，最靠谱的办法就是重启解释器，然后再次导入该模块


