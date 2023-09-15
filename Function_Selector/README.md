# 函数选择器

调用智能合约时，传递给合约的数据的前4个字节指明要被调用的函数，被称为“函数选择器 Selector”。
函数选择器是函数签名的keccak哈希后的前4个字节。

#### 1.函数签名
函数签名 = 函数名(逗号分隔的参数类型)
其中 uint 和 int 要写为 uint256 和 int256

例如 function transfer(address _to, uint _value) 的函数签名是 transfer(address, uint256)

#### 2.函数选择器
selector = bytes4 ( keccak256 ( 函数签名 ) )

``` js
    function getSelector(string calldata _func) external pure returns (bytes4) {
        return bytes4(keccak256(bytes(_func)));
    }
```
