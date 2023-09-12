# 事件

事件 Events 允许向区块链写入内容，消耗少量的 gas。
应用场景包括：
- 响应前端事件
- 一种廉价的存储方式

事件需要先定义：
``` js
    event Log(address indexed sender, string message);
    event AnotherLog();
```
- 标注 indexed 的参数将存储为哈希值，可以用 filter 快速查找
- 每个事件最多可以有3个标注 indexed 的参数
- message 存储在 data 部分，不能被检索，能保存复杂数据，消耗gas少

然后释放：
``` js
    function test() public {
        emit Log(msg.sender, "Hello World!");
        emit Log(msg.sender, "Hello EVM!");
        emit AnotherLog();
    }
```