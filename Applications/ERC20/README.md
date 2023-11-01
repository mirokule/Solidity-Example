#### ERC20

全称为 Ethereum Request for Comments 20，于2016年9月正式发布。
ERC20 定义了一套规则和接口，使不同的代币可以相互交换和使用。
##### 函数
- totalSupply()：返回代币的总供应量
- balanceOf(address _owner)：返回指定地址的代币余额
- transfer(address _to, unit256 _value)：向目标地址转移指定数量的代币
- transferFrom(address _from, address _to, uint256 _value)：从源地址转移代币
- approve(address _spender, uint256 _value)：授权目标地址使用指定数量的代币
- allowance(address _to, address _spender)：拥有者已经授权给使用者的代币数量

##### 事件
- event Transfer：当代币转移时触发
- event Approval：当代币被授权时触发