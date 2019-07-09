# Clean code

> 书名: 《代码整洁之道》 
<br>
> 作者:  Robert C. Martind

### 读书简记

1. [变量的命名](https://github.com/zhaotianxiang/code-standards/blob/master/name.md)
2. [函数的写法](https://github.com/zhaotianxiang/code-standards/blob/master/function.md)
3. [注释的写法](https://github.com/zhaotianxiang/code-standards/blob/master/comments.md)
4. [错误处理](https://github.com/zhaotianxiang/code-standards/blob/master/error.md)


### 整洁代码概述

1. Reading more than writing: when you are working in a mature system, you may spend more time reading code than writing new code, since a lot of things has already been implemented before and you just need to know their existence and how to use them correctly. From another perspective, the code you write will also be read and used by other people. So it is very important to write code that are easy to read, **reuse and enlarge**.

2. Divide big class into small classes: A class is, by it’s name, a category. The class should only contain variables and methods that are mutually dependent on each other. If some part is an independent concept and does not depend on other parts of the class, that part should be separated out to be another class or enum or something. The rest of the class can still use the separated class by an instance. See example in chapter 16.

3. A bunch of small classes is more organized for readers: In chapter 16, the SerialDate class originally has 1000 lines of code. It was really big. It contains too much information and is poorly organized. Readers will have a hard time figuring out the logic of the things going on there. But actually, the big class SerialDate contains informations and methods of Week, Month, etc. It can be seen that SerialDate depends on Week and Month information to determine what date it is. But Week doesn’t depend on SerialDate to know Monday is Monday. This is not a mutual dependent relationship. Same for that between Month and SerialDate. So, we should make new enums for Week and Month and move related methods out of SerialDate. After the re-organizing, the SerialDate class became shorter. It is easier for the reader to track the relationship of several small classes than figuring out a long and inclusive big class. See example on P349.

4. Less comments, use expressive names: Comments are hard to maintain and easy to be obsolete. Obsolete comments can be misleading. We should make our code express itself instead of relying on comments for other readers to understand. The key point of self explaining code is expressive name.

5. Abstraction level of names: the names of the class, variables and methods should describe the things to an appropriate abstraction level. You can explain the method in human language, like making a summary of the things the method does. Then the summary will be the name of the method. When making a summary, you won’t be interrupted by the details of implementations. But rather it is like describing the chain of purposes and outcomes. The name of the method should tell the user what he can expect for the outcome and also conditions of usage(which are what a user cares about). But not the specific implementation details. When the system is huge, you don’t require everyone knows everything in order to make the system running. Responsibilities should be separated and encapsulated. When a user uses your method, he doesn’t care about the implementation. He only needs to care about what goal can this method achieve for him, and if there are some important conditions of usage(or side effects) he needs to know in order to call the right method. So these two things should be expressed in the method name.

6. Small method: a method should do one and only one thing. only when this is fulfilled, can we find reasonable length expressive name for the method. If a method does too many things, it is hard to find a short summary for it. When you describe what your method do, try to break the logic down when a deeper level of abstraction is needed(more specific implementation details). That’s when another method should be created.

7. Only one level of abstraction down in the method implementation: each method should contains the code that is only one level down (one level more specific than) the name of the method(the summary of the method). Further level down should be put into another method that is called by this method.

8. No duplication: There are two things you can do to prevent duplication. First, make the classes and methods small and remove unnecessary coupling between them. Second, use polymorphism to replace repeated switch/if else cases. When switch/if else happens, usually it means same purpose but different implementations for different conditions. The purpose sounds like the name of the method. So, same method name, different implementations. What does this sound like? Polymorphism! When repeated switch/if else cases for a same set of conditions happen, it is better to created several classes according to the switch condition. The super class of those classes has abstract method with a name that is common to all subclasses. The subclasses will have unique implementations. Then the switch statements will be greatly shortened, just like instance.methodName(). The computer will automatically find out what subclass is the intense and what specific implementation should be called. This way, the switch statements become implicit and automatic. What’s better, the abstract method contract is that subclasses must implement it. But the compiler cannot force a programmer not forgetting to complete all the switch statements. So the contract makes the code more robust and less error prone. Polymorphism makes it more flexible in the appearance of the code(less condition judgement classification) and it does some automatic forced contract for us to make sure we call the right specific code we intend to.

9. The sign of using polymorphism: when you find that for different conditions, you need to do a same set of things(same purpose method). The conditions will be categorization reasons. If in the methods for different conditions with same purpose, you find the logic is really similar and just some variable type are different, then polymorphism is really the right thing to do. Because variable type is like different subclasses. Same logic means same method names, which means polymorphism overridden abstract methods. See example in chapter 14.

10. Difference between switch statements and polymorphism class: when using switch statements, behaviors under a certain condition are scattered around. But when using polymorphism and subclasses, we organize all the states and behaviors under a certain condition into one place. An object is not just a int, a boolean, a data container. An object is a more powerful aggregation that is capable of hold states and exert behaviors. Less scattered around different types simple data containers. Less duplicated logic and code. See example in chapter 14.

11. Limitation of polymorphism: overloaded methods must have same return type and same argument list. When the return types of different subclass methods are different, the naming contract provided by polymorphism cannot be used. See example in chapter 14 on P196.

12. Advantage of polymorphism over switch statements: when a new switch condition is added, all the related behaviors can be put together in a new subclass, without changing existing subclasses. And, because the switch statements are handled implicitly and automatically in polymorphism by super class to subclass tracking, the original main body of the code will not need to be changed. Or at least a lot less areas will need to be changed. See example in chapter 14 on P238.

13. No abuse on abstract method: when you find subclasses will have similar code logic for a certain abstract method, it’s time to consider move those code(implementation) up to the super class and make the method concrete. Inside that concrete method, polymorphism of abstract method being called can be used. This will reduce duplication. See example in chapter 16 on P282.

14. No abuse on static method: instance method is open for polymorphism. The same name different implementation contract is built in polymorphism of instance method. Instance method has this flexibility of polymorphism over static method. See P296.

15. Use Factory to dedicate on creating instance: separate code for object creation and application of it. See example on P403.

16. Encapsulate boundary: sometimes the code has +1,-1 boundary adjustments. Don’t let those +1,-1diffuse every where. Encapsulate them in a method or one place during assignment to a variable. And use the encapsulation in other places. You want only one place to see and change the boundary condition. See example in chapter 15 on P261.

17. Meaningful name for constants: Don’t directly diffuse numbers in the code. Especially when the meaning of the number is not clear to readers and when the values could get changed. It’s hard to locate all the 5 and refactor them all in the code when you  want to change the value. But it is easy to locate and refactor the variable: nameOfConstant.

18. Encapsulate the code that needs mocking during unit test: during the internship, using mockito to mock the behavior of data accessing to the database is the pain in the ass. Dependency injection is a good way to know the object being mocked before the mocking begins. It makes the mocktio test writing so much easier. Another thing I recently thought about is that I should have encapsulate data accessing code into specialized methods and separate them from the other code in the method that doesn’t need mocking during testing. But I think dependency injection from the argument of the method is still the key that makes my mockito test writing much easier. But encapsulating will make the parts more clear.

19. Write tests before production code implementation: when there is nothing to be mocked during unit test, the test code should be easy to determine before the implementation of production code. As long as we know the input, output and method name, we can expect for a set of behaviors and write test first. Even when there are methods that contains data store accessing and need to be mocked during unit test, we can still write the test code before production code. Here is the power of encapsulation: you can choose the name of the encapsulator by yourself. You encapsulate the code of data store accessing in the encapsulator. Before the implementations of those data store accessing code, although you don’t know the exact code for those, you do know the name, input and output of the encapsulator. So you know the name of the method you want to mock during unit testing, which is the name of the encapsulator. As for the unit test for the encapsulator, we can wait after the encapsulator is implemented.

20. Unit tests should not depend on each other: if the order of tests execution matters, or some variable are shared, then when you change one test, you may break another. Make them independent.

21. Tests also need to have clean pattern: the requirements and principles of writing test is the same with writing production code. Name the variables and methods nicely. Write small methods. When necessary, write helper method that encapsulate some low level details.

22. Boundary management between my code and other people’s code: A big project is divided into several parts for different people to work on individually first and combine later. Without having their implementations done, you can define boundary encapsulation APIs that define your wanted input and output. What those encapsulation APIs really reflect and represent is your need and purpose, which should be satisfied in order to make the system work no matter what. Instead of directly using other people’s APIs and let them diffuse into your own code, you encapsulate their APIs into your boundary encapsulators. Only your boundary encapsulators diffuse into your own code. In this way, if other people decide to change the format of their APIs, the only part of your code that needs to change accordingly is the boundary encapsulators. See chapter 8 P119.
...

### 参考
1. [知乎回答-关于《代码整洁之道》问题、看法和疑问？](https://www.zhihu.com/question/27603872)
<br/>
2. [JavaScript 规范](https://github.com/alivebao/clean-code-js#%E4%BB%8B%E7%BB%8D)
