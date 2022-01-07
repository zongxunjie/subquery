03*必填在本节课中，我们介绍了SubQuery 如何处理什么内容？

A.Mapping function


B.实体关系


C.默认数据源


D.自定义数据源

D

04*必填请用一句话概括使用自定义数据源的原因？
特定区块链中，数据结构混合多层，无法直接解析、过滤、调用等，需要定制化。


05*必填本节课我们使用了哪个链上的 EVM 数据 进行了演示？
moonriver

06*必填处理substrate/Moonbeam的数据源类型，我们需要一个什么？

Processor


Handler


Transformer


Decoder

A 

07*必填为了处理合约类型的 Event，SubQuery 提供了 一个名为 @subql/
 的 Package。
 subql/contract-processors
 
08*必填请解释在 Assets 中，我们定义 ERC20 以及路径 ./erc20.abi.json 的意义
提供通用ERC20数据结构，解析索引下来的ERC20数据

09*必填在 Mapping Handler 中，我们定义了处理自定义数据源是什么类型？提示，Substrate/___Event
substrate/MoonbeamEvent

10*必填在上题中这类数据中，课我们过滤了的哪个 Topic？以及它的接口是什么样的？
Transfer(address indexed from, address indexed to, uint256 value)

11*必填在 Mapping 中，我们提到另外一种创建一个新的实体的方法是什么？
export async function erc20Transfer(event: MoonbeamEvent<[string, string, BigNumber] & {from:string, to:string, value:BigNumber}>): Promise<void> {...}

12*必填请查询 Transaction Hash 为 0xfffc3ba5ee18d70cde32b3f680f200f7a129a044535e6378eddc2dcbeed717bf 的转账金额。
500039404066484530634