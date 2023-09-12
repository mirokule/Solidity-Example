# 函数修饰符

修饰符 view 和 pure 可以节省gas，并控制函数权限。

- view：不修改任何状态变量，仅读取
- pure：不修改、不读取任何状态变量，例如某些工具函数

``` js
    uint public x = 1;

    function addToX(uint y) public view returns (uint) {
        return x + y;
    }

    function add(uint i, uint j) public pure returns (uint) {
        return i + j;
    }
```