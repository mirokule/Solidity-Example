# 常量修饰符

- constant
    - 必须在声明时初始化，将初始值硬编码
    - 不是状态变量，不储存在插槽(slot)里

``` js
    address public constant MY_ADDRESS = 0x777788889999AaAAbBbbCcccddDdeeeEfFFfCcCc;
    uint public constant MY_UINT = 123;
```

- immutable
    - 可以在声明、构造函数中赋值
    - 是状态变量，储存在插槽(slot)里

``` js
    address public immutable MY_ADDRESS;
    uint public immutable MY_UINT;

    constructor(uint _myUint) {
        MY_ADDRESS = msg.sender;
        MY_UINT = _myUint;
    }
```
