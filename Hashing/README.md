# 哈希函数

Keccak256是哈希函数的一种，可以将任意长度的数据转换为256位的哈希值。
使用 SHA-3 算法，比 SHA-2 更加安全和先进。

哈希函数的特点：
- collision resistance：很难找到一对X和Y，使得H(X)=H(Y)
- hiding：计算过程单向不可逆，无法从H(X)反推出X
- puzzle friendly：对于输入X，无法提前预测H(X)的取值区间

``` js
    function hash(
        string memory _text,
        uint _num,
        address _addr
    ) public pure returns (bytes32) {
        return keccak256(abi.encodePacked(_text, _num, _addr));
    }
```