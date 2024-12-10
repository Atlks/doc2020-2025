以太坊PHP离线交易开发包
Created 4 years ago by jimilai, Updated 4 years ago    Revision #1    10361 views    0 likes    0 collects

EthTool开发包适用于希望采用裸交易的PHP以太坊应用开发，主要包含以下特性：
支持裸交易部署/调用合约
内置etherscan和infura支持
keystore生成与读取，兼容geth/parity
采用裸交易的一个好处是开发者不必自己部署以太坊节点 —— 同步区块是很痛苦的过程。使用EthTool构造 好裸交易之后，只需要使用第三方（etherscan/infura/...）提供的服务来广播交易即可。


EtherscanProvider 及InfuraProvider: 如果没有自己的节点，可以使用Etherscan 及Infura 的Provider，他们都是以太坊的基础设施服务提供商

Apply a token api ,,then can invoke..

1.什么是Infura？
专业一点讲，Infura是一种IaaS（Infrastructure as a Service）产品，目的是为了降低访问以太坊数据的门槛。
通俗一点讲，Infura就是一个可以让你的dApp快速接入以太坊的平台，不需要本地运行以太坊节点。
从程序员的角度讲，Infura就是一个Web3 Provider，背后是负载均衡的API节点集群。使用它的好处就是，你永远不必担心连接的节点失效的问题，Infura会管理好这一切。
另外，也是非常重要的一点：Infura目前是免费的。


web3 使用裸交易 | PHP实现ETH 3

