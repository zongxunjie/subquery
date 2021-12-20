
03*必填在本节课中，我们重点讲解subquery项目的哪内容？

A、Mapping function


B、schema.graphql


C、manifest


D、一对多关系

A

04*必填默认datasource 的映射，我们支持处理哪三种数据？多选

A、block


B、event


C、extrinsic


D、evm

A B C

05*必填如何通过单一polkadot api调取这个某个账户的转账历史？

A、api.chain.system.account(Address)


B、api.query.system.account(Address)


C、api.query.system.transfer(Address)


D、不存在这个方法

D

06*必填在polkadot js上进行批次转账的方法是 ？

A、balances.transferAll


B、utility.BatchAll


C、balance.forceTransfer


D、balance.transfer

B

07*必填请指出，我们为了检索个人账户的转账历史，提供了哪两种方案？
方案一：检索balances.transfer
方案二：检索所有关联类型extrinsics:
* balances.forceTransfer
* balances.transfer
* balances.transferAll
* balances.transferKeepAlive
* Utility模块下所有可能进行的以上calls

08*必填手动调取区块高度上的event数据，我们依赖了哪个package？
@polkadot/api

09*必填我们通过手动调取的balance.transfer 数据， 他们的chain type 类型分别是什么，请按顺序写出。

T::AccountId
T::AccountId
T::Balance


10*必填我们提供了包装过的后的block，和event及extrinsic类型，他们的类型名字是什么？

SubstrateBlock、SubstrateEvent、SubstrateExtrinsic


11*必填在包装过后的event 类型，还添加了哪些额外可访问的属性？多选

timestamp: number


*idx: number;


*extrinsic?; SubstrateExtrinsic


*block: SubstrateBlock

B C D

12*必填假如，我们已经创建了实体 const record = new Transfer(’2021123-1‘), 我们将如何保存这个实体 ？
await record.save()


13*必填在第二种方案中，我们替换了首先替换了manifest中的哪些内容？
handlers:
  - handler: handleTransfer
    kind: substrate/CallHandler
	fiter:
	  module: balances
	  method: transfer
	  success: true
  - handler: handleForceTransfer
    kind: substrate/CallHandler
	fiter:
	  module: balances
	  method: forceTransfer
	  success: true
  - handler: handleTransferAll
    kind: substrate/CallHandler
	fiter:
	  module: balances
	  method: transferAll
	  success: true
  - handler: handleTransferKeepAlive
    kind: substrate/CallHandler
	fiter:
	  module: balances
	  method: transferKeepAlive
	  success: true
  - handler: handleUtilityBatch
    kind: substrate/CallHandler
	fiter:
	  module: utility
	  method: batch
	  success: true
  - handler: handleUtilityBatchAll
    kind: substrate/CallHandler
	fiter:
	  module: utility
	  method: batchAll
      success: true	  


14*必填在第二种方案中，我们是否可以避免检索 batch 模块？为什么？这样做有什么影响
不能，不知道在这个批次中是否有相关的transfer extrinsic，直到检索了它

15*必填在我们的方案中，列出至少两条索引event要优于extrinsics的原因

1. 只需关注特定的event类型，数据格式稳定
2. 使用extrinsics需要覆盖触发event的所有extrinsic，数据格式不统一，可能会跟runtime升级发生变化,导致没有及时更新mapping错过检索
3. 不能够保证utility模块中包括了transfer类型的extrinsics，间接触发和批次触发
4. 谨慎处理多层递归

16*必填编程题，我们在schema 中定义了如下的实体（图1），请尝试完成在mapping 中的方法，处理staking.Reward 这个event ，通过实体接口保存至数据库（图2）

schema文件
type transfer @entity {
	id: ID!

	from: String!

	to: String!

	amount: BigInt!
}

mappings/mappingHandlers.ts文件

import {SubstrateExtrinsic, SubstrateEvent, SubstrateBlock} from "@subql/types";
import {StakingReward} from "../types";
import {Balance, AccountId} from "@polkadot/types/interfaces";

export async function handleStakingReward(event: SubstrateEvent): Promise<void> {
	
	
	const {event: {date: [account,balance]}} = event;
	const entity = new StakingReward(`${event.block.block.header.number}--${event.idx.toString()}`);
	
	entity.address = (account as AccountId).toString();
	entity.balance = (balance as Balance).toBigInt();
	entity.date = event.block.block.timestamp;
	
	await entity.save();
}
/*
export async function handleTransfer(event: SubstrateEvent): Promise<void> {
	const record = new Transfer(`${event.block.block.header.number.toString()}--${event.idx}`)
	
	const {event: {date: [fromAccount, toAccount, amount]}} = event;
	
	
	record.from = (fromAccount as AccountId).toString();
	record.to = (toAccount as AccountId).toString();
	//Big integer type Balance of a transfer event
	record.amount = (amount as Balance).toBigInt();
	await record.save();
}



//Handle extrinsic balances.tranfer
export async function handleTransfer(call: SubstrateExtrinsic): Promise<void> {
	const record = new Transfer(`${call.block.header.number.toString()}--${call.idx}`)
	const [toAccount, amount] = call.extrinsic.args
	record.from = call.extrinsic.signer.toString();
	record.to = (toAccount as AccountId).toString()
	record.amount = (amount as Balance).toString();
	await record.save();
}

export async function handleForceTransfer(SubstrateExtrinsic): Promise<void> {}
export async function handleTransferAll(SubstrateExtrinsic): Promise<void> {}
export async function handleTransferKeepAlive(SubstrateExtrinsic): Promise<void> {}
export async function handleUtilityBatch(SubstrateExtrinsic): Promise<void> {}
export async function handleUtilityBatchAll(SubstrateExtrinsic): Promise<void> {}
*/

点击添加文件 或将文件拖至此处
文件大小限制: 20MB

17你认为本节课的课程体验如何？可以从老师录课的方式及课程内容质量、作业等方面给出相应的建议。

