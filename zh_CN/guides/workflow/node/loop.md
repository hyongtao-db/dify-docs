# 循环

## 简介

循环（Loop）节点用于执行依赖前一轮结果的重复任务，直到满足退出条件或达到最大循环次数。

## 循环节点与迭代节点有什么区别？

循环节点和迭代节点在任务处理上的定位不同：

<table>
  <thead>
    <tr>
      <th>类型</th>
      <th>特点</th>
      <th>适用场景</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>循环</strong>（Loop）</td>
      <td>轮次之间存在依赖关系的优化型任务。即任务的每一轮执行都依赖上一轮的结果。</td>
      <td>需要前一轮的计算结果，适用于递归、优化问题等。</td>
    </tr>
    <tr>
      <td><strong>迭代</strong>（Iteration）</td>
      <td>轮次之间无依赖关系的批处理任务。即每一轮任务可以独立运行，无需依赖前一轮。</td>
      <td>每轮独立执行，可用于数据批量处理等。</td>
    </tr>
  </tbody>
</table>

## 如何配置循环节点？

循环节点包含以下两个关键配置项：

<table>
  <thead>
    <tr>
      <th>配置项</th>
      <th>作用</th>
      <th>示例</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>循环退出条件</strong>（Loop Termination Condition）</td>
      <td>设置循环何时停止</td>
      <td>例：当变量 <code>x < 50</code> 时，停止循环。</td>
    </tr>
    <tr>
      <td><strong>最大循环次数</strong>（Maximum Loop Count）</td>
      <td>限制最多执行的轮次，避免无限循环</td>
      <td>例：最多执行 10 轮，不管是否满足退出条件。</td>
    </tr>
    <tr>
      <td><strong>循环变量</strong>（Loop Variables）</td>
      <td>用于在循环的不同轮次间传递数据，并在循环结束后继续供下游节点使用</td>
      <td>例：变量 <code>x < 50</code> 在每轮循环中递增 1，循环体内部可以基于 <code>x < 50</code> 进行计算，循环结束后，<code>x < 50</code> 的最终值可用于后续流程。</td>
    </tr>
    <tr>
      <td><strong>退出节点</strong>（Exit Loop）</td>
      <td>用于强制终止循环，一旦执行到此节点，循环立即结束</td>
      <td>例：最多执行 10 轮，不管是否满足退出条件。</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
**退出节点** 与 **循环退出条件** 均可作为循环的终止触发点，满足任意一个条件时，循环都会提前退出。如果未配置任何退出条件，则循环将持续运行（相当于 while (true)），直到达到 **最大循环次数**。
{% endhint %}

![Loop Node](https://assets-docs.dify.ai/2025/03/ba1b3a0150d40bf5cc331f2877717046.png)

![Exit Loop](https://assets-docs.dify.ai/2025/03/d4d354dcc37488efc7ce8d405488a314.png)

## 示例：如何使用循环节点？

**需求：生成 1-100 的随机数，直到随机数小于 50 时停止。**

**实现步骤**：

1. 使用 `code` 节点生成 `1-100` 的随机数。  

2. 使用 `if` 节点判断随机数是否小于 `50`：

   - 如果小于 50，输出 `done` 并结束循环。

   - 如果不小于 50，继续循环，生成新的随机数。

3. 设置循环退出标准：随机数 `< 50`。

4. 循环将在随机数小于 `50` 时自动停止。

![Case steps](https://assets-docs.dify.ai/2025/03/b1c277001fc3cb1fbb85fe7c22a6d0fc.png)