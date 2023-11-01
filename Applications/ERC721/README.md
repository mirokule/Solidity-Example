#### ERC-721

Ethereum Request for Comments 721，为创造非同质化代币（Non-Fungible Token Standard）而制定的标准。
定义了一套核心功能和事件，要求代币必须实现这些功能，以确保跟以太坊网络上的各种钱包、市场和智能合约兼容。
##### 函数
- balanceOf（address）：返回特定地址所拥有的NFT数量
- ownerOf(uint256)：返回特定NFT所有者的地址
- safeTransferFrom(address, address, uint256)：安全地将一个NFT从一个地址转移到另一个地址
- transferFrom(address, address, uint256)：将一个NFT从一个地址转移到另一个
- approve(address, uint256)：批准一个特定的地址管理一个NFT
- getApproved(uint256)：返回当前被批准管理特定NFT的地址
- setApprovalForAll(address, bool)：授予或撤销对一个地址的批准，以管理发件人拥有的所有NFTs
- isApprovedForAll(address, 地址)：检查一个地址是否被批准管理另一个地址所拥有的所有NFT

##### 事件
- Transfer(address, address, uint256)： 当NFT从一个地址转移到另一个地址时
- Approval(address, address, uint256)： 当NFT的所有者批准另一个地址来管理它时
- ApprovalForAll(address, address, bool)： 当一个地址授予或撤销对另一个地址管理其所有NFT的批准时