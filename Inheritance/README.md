# 继承

1.Solidity 支持多重继承。
多重继承的顺序是重要的，从最基础、最早的合约开始。
继承使用关键字 **is**。

2.允许被子合约重写的函数必须使用关键字 **virtual**。
子合约重写函数时必须使用关键字 **override**。
状态变量不允许重写覆盖，可以用构造函数重新赋值。

3.调用父合约中的函数：
- 直接用名字：A.foo()
- 关键字 super：super.foo() 


``` js
contract A {
    function foo() public pure virtual returns (string memory) {
        return "A";
    }
}

contract B is A {
    // Override A.foo()
    function foo() public pure virtual override returns (string memory) {
        return "B";
    }
}

contract C is A {
    // Override A.foo()
    function foo() public pure virtual override returns (string memory) {
        return "C";
    }
}

contract D is B, C {
    // D.foo() returns "C"
    function foo() public pure override(B, C) returns (string memory) {
        return super.foo();
    }
}
```