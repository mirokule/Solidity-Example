# 调用其他合约函数

调用其他合约的函数有两种方式：
- 使用函数名：A.foo(x,y,z)
- 使用call：不推荐

``` js
    function setX(Callee _callee, uint _x) public {
        uint x = _callee.setX(_x);
    }

    function setXFromAddress(address _addr, uint _x) public {
        Callee callee = Callee(_addr);
        callee.setX(_x);
    }

    function setXandSendEther(Callee _callee, uint _x) public payable {
        (uint x, uint value) = _callee.setXandSendEther{value: msg.value}(_x);
    }
```

#### Delegatecall
跟call类似，都是底层函数。
不同之处在于执行函数时，使用的 context 来自发起合约，而不是被调用合约。
被调用合约只提供函数的逻辑。

``` js
    function setVars(address _contract, uint _num) public payable {
        (bool success, bytes memory data) = _contract.delegatecall(
            abi.encodeWithSignature("setVars(uint256)", _num)
        );
    }
```