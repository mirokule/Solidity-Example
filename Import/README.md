# 引用合约

#### Import
使用Import可以导入本地或外部合约：
- 本地 import “./ye.sol”;
- 网络 import ‘https://github.com/ye.sol';
- npm import ‘@openzeppelin/ye.sol’;
- 全局符号 import {ye} from ‘./ye.sol’;

``` js
import "./foo.sol";

import {Unauthorized, add as func, Point} from "./foo.sol";

import "https://github.com/owner/repo/blob/branch/path/to/Contract.sol";

```


#### Library
库合约可以看做函数集合，与普通合约相比的不同点：
- 不能存在状态变量
- 不能继承或被继承
- 不能接收以太币
- 不可以被销毁

``` js
// 将库合约的函数附加到任何类型
using Strings for uint256;
_number.toHexString();

// 通过库合约的名称调用
Strings.toHexString(_number);
```