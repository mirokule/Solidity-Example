# 发送ETH

发送 ETH 的函数有三个：
- transfer：2300 gas限制，发送失败抛出异常
- send：2300 gas限制，返回结果bool值
- call：没有gas限制，返回结果bool值，能防重入，推荐使用

``` js
contract SendEther {
    function sendViaTransfer(address payable _to) public payable {
        // 不推荐
        _to.transfer(msg.value);
    }

    function sendViaSend(address payable _to) public payable {
        // 不推荐
        bool sent = _to.send(msg.value);
        require(sent, "Failed to send Ether");
    }

    function sendViaCall(address payable _to) public payable {
        // 推荐使用
        (bool sent, bytes memory data) = _to.call{value: msg.value}("");
        require(sent, "Failed to send Ether");
    }
}
```

#### Call
call 是与其他合约交互的基本函数之一，是通过 fallback() 发送ETH的推荐方式。
但也不能滥用，调用目标合约的函数时使用函数名通常是更好的选择。
用法是 **接收方地址.call {value: 发送ETH数额, gas: gas数额 }(二进制编码);**
没有gas限制，有返回值(bool, data)，不自动 revert，需要额外代码处理

``` js
contract Caller {
    event Response(bool success, bytes data);

    // 知道目标合约的地址和函数名时的 call
    function testCallFoo(address payable _addr) public payable {
        (bool success, bytes memory data) = _addr.call{value: msg.value, gas: 5000}(
            abi.encodeWithSignature("foo(string,uint256)", "call foo", 123)
        );

        emit Response(success, data);
    }

    // call 不存在的函数，将触发 fallback()
    function testCallDoesNotExist(address payable _addr) public payable {
        (bool success, bytes memory data) = _addr.call{value: msg.value}(
            abi.encodeWithSignature("doesNotExist()")
        );

        emit Response(success, data);
    }
}
```