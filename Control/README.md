# 控制语句

JavaScript 中的大部分控制语句在 Solidity 中都是可用的，除了 **switch** 和 **goto** .
关键词 if, else, while, do, for, break, continue, return, ?: 与JavaScript语义相同。

``` js
    function foo(uint x) public pure returns (uint) {
        if (x < 10) {
            return 0;
        } else if (x < 20) {
            return 1;
        } else {
            return 2;
        }
    }


    function loop() public {
        for (uint i = 0; i < 10; i++) {
            if (i == 3) {
                continue;
            }
            if (i == 5) {
                break;
            }
        }

        uint j;
        while (j < 10) {
            j++;
        }
    }

```