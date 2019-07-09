# 变量命名法则

 **Meaningful Names**


### Good Gay

1. 名副其实: 阅读名称就知道它为什么存在，做什么事，应该怎么用，如果需要通过注释来回答，那就不算名副其实。

2. 不容易混淆: 避免使用非常相似的名称，尤其是类型还相同时， 尽量保持名称有很大的差异。

3. 不怕长: 不要因为害怕名称过长而使用缩写，那样不便于和别人讨论。

4. 认真的对待每一个变量名，你当用为自己的第一个孩子命名般的谨慎来给变量起名。 

5. 代码即设计， 简单代码。 抽象即恶，Abstraction Descant

6. 不要做 **代码猴子** 【Code Monkey】 "可以运行"的代码不一定是好代码， Secrets for Going Fast whitout Making a Mess;

7. 整洁的代码只做好一件事。 整洁的代码优雅， 外表和举止都令人愉悦， 精致而且简单.

### Bad Gay

1. wading is no way / Later is never.  烂程序没有之后修改的可能， 要一次性写好。 无论多么急， 花时间保持代码整洁， 不但关乎效率， 而且关乎生存。

2. 变量名称有1,2, one, two... 这类标志同一种抽象的不同实例。

### 命名原则

1. 名副其实

   - 指明计量对象和计量单位

'''c
int daySinceCreation
'''

   - 代码的简洁性/模糊性，分清楚什么类型/下标的意义/整数值的意义/怎么使用这个类型？ 
   - 什么是幽灵变量和魔术数字， 避免使用。
   - 多含义和单平台的变量名称不好。

2. 做有意义的区分
   - 废话就是做没有意义的区分： a1,a2,a3
   - productInfo/productData  a/an/the
   - Variable 废话应该永远不能出现在变量中
   - Table 永远不要出现在表名中
   - customerInfo 和 customer 没有任何区别
   - accountData 和 account 没有任何区别
3. 使用读的出来的名称，千万不要自造词
4. 使用可搜索的名称， 常量的搜索太难了。 const int WORK_DAYS_PER_WEEK=5
5. 避免使用编码
6. 更小的类， 更短的方法， 使得每一个变量的定义都在视野范围之内。
7. 不必用成员前缀m来标示 成员变量 应该把类和函数做的足够小
8. 避免映射思维
   - 使用问题领域的术语， 还是使用解决方案的术语。
   - 明确是王道。
9. 类名
   - 类名不应该是动词， 而应该是名词， 而且应该有点儿抽象。
10. 方法名
   - 方法名应该是动词或者动词短语
   - 别卖萌，如 eatMyShorts() === abort()
11. 每个概念对应一个词
12. 永远别用双关语 insert or append but not add
13. 使用解决方案领域的名称作为变量
14. 使用源自所涉及问题领域的名称
15. 添加有意义的语境 ~~firstName~~ ~~lastName~~ ~~houseNumber~~, ~~state~~,  addrFirstName, addrLastName.

**取名字最难的地方在于需要良好的描述技巧和共有文化背景，与其说是一种技术,商业，管理的问题， 不如说时一种教学问题。**

### 5S编程哲学

 - Seiri        整理
 - Seton        整齐/整洁   
    - A place for everything, and everything in its place
    - Cleanliness is next to godliness
    -  
 - Sesio        清楚
 - Seiketsu     清洁
 - Shitsuke     身美/自律
    - A stitch in time save nine
    - Mighty oaks from little acrons grows
