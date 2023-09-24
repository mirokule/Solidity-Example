# ABI：Application Binary Interface

ABI是一套**编码**和**解码**的规范，是与智能合约交互的标准。

函数包括：
- encode：将每个参数填充为32字节的数据，并拼接在一起，可以与合约交互
- encodePacked：将填充的 0 省略，可以节省空间，但不能与合约交互
- encodeWithSignature：第一个参数为函数签名，调用其他合约时使用
- encodeWithSelector：第一个参数为函数选择器，需完成从 函数签名 -> 函数选择器 的过程
- decode：解码 encode 生成的二进制编码，还原成原本的参数

``` js
    function encode(uint x, address addr, uint[] calldata arr, MyStruct calldata myStruct)
        external pure returns (bytes memory) {
        return abi.encode(x, addr, arr, myStruct);
    }

    function decode(bytes calldata data)
        external pure returns (uint x, address addr, uint[] memory arr, MyStruct memory myStruct) {
        (x, addr, arr, myStruct) = abi.decode(data, (uint, address, uint[], MyStruct));
    }

    function encodeWithSignature(address to, uint amount) 
        external pure returns (bytes memory) {
        return abi.encodeWithSignature("transfer(address,uint256)", to, amount);
    }

    function encodeWithSelector(address to, uint amount) 
        external pure returns (bytes memory) {
        return abi.encodeWithSelector(IERC20.transfer.selector, to, amount);
    }

    function encodeCall(address to, uint amount) external pure returns (bytes memory) {
        return abi.encodeCall(IERC20.transfer, (to, amount));
    }
```