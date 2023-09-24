# 变量

根据作用域的不同，分为3种：
- 局部变量 local：函数内成员，内存中，不上链，gas消耗低
- 状态变量 state：合约成员，在链上，gas消耗高
- 全局变量 global：预留的关键字，提供全局信息，比如 msg.sender, block.number 等

``` js
contract Variables {
    // 状态变量
    string public text = "Hello";
    uint public num = 123;

    function doSomething() public {
        // 局部变量
        uint i = 456;

        // 全局变量
        uint timestamp = block.timestamp;
        address sender = msg.sender; 
    }
}
```