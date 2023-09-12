# 异常

异常被抛出时，所有对状态变量的修改将会回撤。
异常可以通过3种方式抛出：
- require：可以带描述异常的字符串，消耗gas多
- revert：可以像require一样用字符串；也可以自定义error，用error名称替代描述异常的字符串，从而降低gas消耗
- assert：不能带描述异常的字符串，消耗gas少

``` js
    // require
    function testRequire(uint _i) public pure {
        require(_i > 10, "Input must be greater than 10");
    }

    // revert 的用法一：等同于 require
    function testRevert(uint _i) public pure {
        if (_i <= 10) {
            revert("Input must be greater than 10");
        }
    }

    // revert 的用法二：通过自定义 error，降低 gas 消耗
    error InsufficientBalance(uint balance, uint withdrawAmount);

    function testCustomError(uint _withdrawAmount) public view {
        uint bal = address(this).balance;
        if (bal < _withdrawAmount) {
            revert InsufficientBalance({balance: bal, withdrawAmount: _withdrawAmount});
        }
    }

    // assert
    function testAssert() public view {
        assert(num == 0);
    }
```