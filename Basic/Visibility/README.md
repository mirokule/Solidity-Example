# 可见性

函数和变量都可以声明可见性，以控制访问权限。
- public：默认方式，内外均可调用
- private：只能在当前合约访问，继承的合约不行
- internal：只能在当前合约、继承的合约中访问
- external：只能从外部访问

状态变量不能被声明为 external

``` js
    function privateFunc() private pure returns (string memory) {
        return "private function called";
    }

    function testPrivateFunc() public pure returns (string memory) {
        return privateFunc();
    }

    function internalFunc() internal pure returns (string memory) {
        return "internal function called";
    }

    function externalFunc() external pure returns (string memory) {
        return "external function called";
    }
```