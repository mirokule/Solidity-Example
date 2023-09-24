# 结构

结构可以在合约之外声明，并通过 import 语句在其他合约中使用。

``` js
struct Todo {
        string text;
        bool completed;
    }

    Todo[] public todos;

    // 初始赋值的3种方式
    function create(string calldata _text) public {
        // 1.类构造函数
        todos.push(Todo(_text, false));

        // 2.键值对
        todos.push(Todo({text: _text, completed: false}));

        // 3.初始化空结构，然后赋值
        Todo memory todo;
        todo.text = _text;
        // todo.completed 布尔值初始化默认 false

        todos.push(todo);
    }
```