03*必填什么样的字段适合加索引？
条件筛选字段

04*必填什么情况是无法使用字典来进行加速的？
每个区块或每个event都要处理时

05*必填如何打开 Profiler 模式？
在docker-compose.yml文件中添加
command:
  - --profiler

06*必填以下哪个选项不能加快项目索引速度？

使用字典


使用更快的API Endpoint


使用更高配置的机器


增加很多的数据库索引

D

07*必填用 store.bulkCreate 和 Promise.all 哪个效率更高？
store.bulkCreate