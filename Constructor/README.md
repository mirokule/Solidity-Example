# 构造函数

构造函数在合约创建时执行一次。
如果不自定义构造函数，合约将执行默认的构造函数。
如果父合约的构造函数有参数，子合约应提供这些参数。

``` js
contract X {
    string public name;

    constructor(string memory _name) {
        name = _name;
    }
}

contract Y {
    string public text;

    constructor(string memory _text) {
        text = _text;
    }
}

// 子合约提供父合约构造函数参数的方法有两种：
contract B is X("Input to X"), Y("Input to Y") {

}

contract C is X, Y {
    constructor(string memory _name, string memory _text) X(_name) Y(_text) {}
}

```