# 修饰器

修饰器 Modifier 可以在函数执行之前，或之后运行。
通常用来：
- 限制访问
- 验证输入
- 防止重入攻击

修饰器中用下划线“_”，指代被修饰的函数代码。

示例一：验证调用者身份、输入合法性
``` js
    modifier onlyOwner() {
        require(msg.sender == owner, "Not owner");
        _;
    }

    modifier validAddress(address _addr) {
        require(_addr != address(0), "Not valid address");
        _;
    }

    function changeOwner(address _newOwner) public onlyOwner validAddress(_newOwner) {
        owner = _newOwner;
    }
```

示例二：防止重入攻击
``` js
    modifier noReentrancy() {
        require(!locked, "No reentrancy");

        locked = true;
        _;
        locked = false;
    }

    function decrement(uint i) public noReentrancy {
        x -= i;

        if (i > 1) {
            decrement(i - 1);
        }
    }
```