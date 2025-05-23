# 什么是数组变量？

数组变量是一种特定的数据类型，变量内通常包含多个元素。其中的元素用逗号分隔，以 `[` 开头，以 `]` 结尾。例如：

**数字型：**

```
[0,1,2,3,4,5]
```

**字符串型：**

```
["Monday", "Tuesday", "Wednesday", "Thursday"]
```

**JSON 对象：**

```
[
    {
        "name": "Alice",
        "age": 30,
        "email": "alice@example.com"
    },
    {
        "name": "Bob",
        "age": 25,
        "email": "bob@example.com"
    },
    {
        "name": "Charlie",
        "age": 35,
        "email": "charlie@example.com"
    }
]
```

### 使用场景

* [工作流 - 列表操作](../../guides/workflow/node/list-operator.md)。列表操作节点可以对文件的格式类型、文件名、大小等属性进行过滤与提取，将不同格式的文件传递给对应的处理节点，以实现对不同文件处理流的精确控制
*   [工作流 - 迭代](../../guides/workflow/node/iteration.md)。针对数组中的元素依次执行相同的操作步骤，直至输出所有结果，可以理解为任务批处理器。





