3.在本节课中，我们将会讲解subquery项目的哪内容？多选

A、清单文件


B、schema.graphql


C、package.json


D、以上都是
A B

4.于课程发布时，我们当前的manifest支持哪些版本？多选

A、0.0.1


B、0.0.2


C、0.1.0


D、0.2.0
A D

5.在manifest中，endpoint 属于哪部分？

A、dictionary


B、project


C、Datasources


D、network
D

6.在startBlock 是否可以随意调整？多选

A、如果数据库里没有这个项目，可以调整


B、随时调整


C、删除项目数据后，重新爬取，可以调整


D、不可以调整

A C

7.除了支持默认的datasource runtime，subql还支持什么类型的datasource？
substrate/CustomDataSource
substrate/Moonbeam

8.默认的datasource 支持哪三种类型的handler？
handleBlock、handleEvent、handleCall

9.三种handler的通用的filter是什么，请列举一种构造形式？
specVersion
- handler: handleCall2
  kind: substrate/CallHandler
  filter:
    specVersion: [25, 100] # Index block with specVersion in between 25 and 100 (inclusive).

10. 在entity 的字段上，使用感叹号的意义是什么
字段后面带感叹号，表示是必填字段

11. Entity 的 id 字段是否可以删除？
不可以，唯一id字段为主键

12. 请写出在某个字段上添加一个索引，并索引唯一的对象。
type User @entiy {
	id: ID!
	name: String! @index{unique: true} # unique can be set to true or false
}

13. 我想在schema上添加新的字段 field2，是否可以调整？多选

A、如果数据库里没有这个项目，项目暂未索引，可以调整


B、随时调整


C、删除项目数据后，重新爬取，可以调整


D、不可以调整

A C

14. Codegen 命令编译的对象储存在哪个文件夹中？
src/types/models/

15. 如果调整了schema，我们是否需要重新codegen？
需要

16如果在实体 StarterEntity 上的字段 myField : string 并添加了一个索引 @index， 在这个对象的类中，将会生成怎样的一个方法去索引对象，并且方法返回类型是什么？
static async getByField(myField: string): Promise<StarterEntity[] | undefined> {
	const records = await store.getByField('StarterEntity', myField);
	return records.map(record => StarterEntity.create(record));
}
