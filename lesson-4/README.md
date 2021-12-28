
03*必填在本节课中，我们重点讲解subquery项目的哪内容？

A、Mapping function


B、Schema.graphql


C、实体关系


D、Manifest

C 

04*必填请列出 subquery所支持的实体关系？
一对一
一对多
多对多

05*必填在本节课，一对多的关系案例讲解中，我们创建了哪几个新的实体？我们替换了哪几个字段的的内容？
Account实体
to: String! -> to:Account!

06*必填例如我们现在有实体A的一个字段是reward，然后它的类型是一个叫做StakingReward的实体，那么实体A在生成的model类中，这个相应字段的属性应该是？
外键类型 rewardId

07*必填我们知道添加的外键都会自动增加索引index，那么在实体生成的类中，提供的getBy的方法，最多可以返回多少个记录？
100条记录

08*必填为什么我们要添加一个makeSureAccount 的方法？ 这个方法要在什么地方触发它？
添加makeSureAccount为了保障Account被关联之前已经存在数据库中，若无法找到会导致报错
触发位置：在保存transfer之前，即await record.save();之前。

09*必填编程题： 为下面的一对多案例中，增加反向查询的字段
type Person @entity {
id: ID!
name: String!
receivedPersonGroup:[PersonGroup] @derivedFrom(field:"person")
}
type PersonGroup @entity {
id: ID!
person: Person!
}


10*必填反向查询会修改数据库表结构吗？
不会

11*必填在subql-node启动，同时清除上一个索引数据记录schema的命令是什么？
subql-node -f . --force-clean

12*必填我们添加在多对多的实战中，为什么要清除一对多的数据库？
表结构发生了变化，需要重新生成，并索引

13*必填我们现在有实体A, 和实体B, 我们希望为它建立多对多关系，那么我们需要怎么做？ 它是一个 中间 表？


14*必填你认为本节课难度如何？

简单


适中


困难



15*必填请问你花费本节课作业时间是多长？

30min内


30min-1h


1h-2h


2h-4h


4h-8h


8h以上

16*必填你认为本节课讲师授课如何？
非常不满意1表示非常不满意非常满意5表示非常满意
17*必填你认为本节课的课程体验如何？可以从老师录课的方式及课程内容质量、作业等方面给出相应的建议。
