# 接口

接口的规则：
- 不能有状态变量
- 不能有构造函数
- 不能继承除接口外的其他合约
- 所有函数必须是 external
- 所有函数不能有实现
- 继承接口的合约必须实现接口定义的所有功能

``` js
// 定义接口
interface ICounter {
    function count() external view returns (uint);

    function increment() external;
}

// 调用接口
// address _counter 是实现了接口的合约地址
contract OtherContract {
    function incrementCounter(address _counter) external {
        ICounter(_counter).increment();
    }

    function getCount(address _counter) external view returns (uint) {
        return ICounter(_counter).count();
    }
}
```