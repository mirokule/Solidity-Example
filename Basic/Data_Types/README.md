# 数据类型
Solidity是一种静态类型语言，每个变量都要在编译时指定类型。

类型分为：
- 数值类型：复制时传递内容，产生新的数据副本
- 引用类型：复制时传递指针，指向同一块数据

数值类型包括：
- 布尔型 bool
- 整型 int / uint
- 地址类型 address：20字节
- 定长字节数组 bytes1, bytes2, ..., bytes32

``` js
    bool public boo = true;

    uint8 public u8 = 1;
    uint256 public u256 = 456;
    uint public u = 123; // uint 等同于 uint256

    address public addr = 0xCA35b7d915458EF540aDe6068dFe2F44E8fa733c;
```

引用类型包括：
- 变长字节数组 bytes[]
- 字符串 string
- 数组 array[]
- 结构 struct
- 映射 mapping