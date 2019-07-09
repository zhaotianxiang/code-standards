# Clean code

> 读《代码整洁之道》有感

1. Reading more than writing: when you are working in a mature system, you may spend more time reading code than writing new code, since a lot of things has already been implemented before and you just need to know their existence and how to use them correctly. From another perspective, the code you write will also be read and used by other people. So it is very important to write code that are easy to read, **reuse and enlarge**.

2. Divide big class into small classes: A class is, by it’s name, a category. The class should only contain variables and methods that are mutually dependent on each other. If some part is an independent concept and does not depend on other parts of the class, that part should be separated out to be another class or enum or something. The rest of the class can still use the separated class by an instance. See example in chapter 16.

3. A bunch of small classes is more organized for readers: In chapter 16, the SerialDate class originally has 1000 lines of code. It was really big. It contains too much information and is poorly organized. Readers will have a hard time figuring out the logic of the things going on there. But actually, the big class SerialDate contains informations and methods of Week, Month, etc. It can be seen that SerialDate depends on Week and Month information to determine what date it is. But Week doesn’t depend on SerialDate to know Monday is Monday. This is not a mutual dependent relationship. Same for that between Month and SerialDate. So, we should make new enums for Week and Month and move related methods out of SerialDate. After the re-organizing, the SerialDate class became shorter. It is easier for the reader to track the relationship of several small classes than figuring out a long and inclusive big class. See example on P349.

4. Less comments, use expressive names: Comments are hard to maintain and easy to be obsolete. Obsolete comments can be misleading. We should make our code express itself instead of relying on comments for other readers to understand. The key point of self explaining code is expressive name.

...

### 目录

1. [变量的命名](https://github.com/zhaotianxiang/code-standards/blob/master/name.md)
2. [函数的写法](https://github.com/zhaotianxiang/code-standards/blob/master/function.md)
3. [注释的写法](https://github.com/zhaotianxiang/code-standards/blob/master/comments.md)
4. [错误处理](https://github.com/zhaotianxiang/code-standards/blob/master/error.md)

### reference
[知乎回答](https://www.zhihu.com/question/27603872)
