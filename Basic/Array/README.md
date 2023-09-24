# 数组

bytes[] 和 string 都是数组
除了定长字符数组如 bytes32 是数值类型外，其他的数组都是引用类型

数组元素的类型以第一个元素为准，如 [uint(1), 2, 3]
如果没有指定类型，则取最小单位，如 [1, 2, 3]的元素类型被认定为 uint8

静态数组：uint[3] _a;
动态数组：uint[] _a;
动态数组可以使用 push() 添加成员

``` js
contract Array {
    // 动态数组
    uint[] public arr;
    uint[] public arr2 = [1, 2, 3];
    // 静态数组，初始化[0, 0...0]
    uint[10] public myFixedSizeArr;

    function get(uint i) public view returns (uint) {
        return arr[i];
    }

    function push(uint i) public {
        arr.push(i);
    }
}
```