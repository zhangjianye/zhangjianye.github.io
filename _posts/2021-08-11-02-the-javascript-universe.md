---
layout: post
title: 02.The javascript universe
date: 2021-08-11
tags: JustJavascript
---

> from https://justjavascript.com/

一开始我们讨论***值***

什么是值？这很难说。

这就类似于在问数学里的数字是什么，或者几何里的点是什么。**值就是 JavaScript 宇宙中的一个东西**。

数字是值 —— 还有些其他的，比如对象和函数。然而，也有许多其他的东西，比如 `if` 语句或者变量声明，都***不是***值。

## 代码和值
在从值开始讨论我的 JavaScript 程序中的所有事情时，我总是想象到《小王子》中的这幅图：

![image](https://user-images.githubusercontent.com/17036920/110733046-3b66db80-8260-11eb-8fa6-dfcc5567678f.png)

我站在一个小行星上 —— 这是我程序中的一段代码。

在它的表面上，我看见了 `if` 语句、变量声明、分号、括号以及其他所有能在 JavaScript 代码中找到的东西。

我的代码包括了一些类似“调用函数”、“重复做这件事许多次”甚至或者“抛出错误”等等指令。我在这些指令之间一步一步地前进 —— 就像在我的小行星上跑来跑去。

> 但我偶尔也会抬头

在一个晴朗的夜空，我看见了不同的值分布在 JavaScript 的天空中：布尔值，数字，字符串，symbol 值， 函数和对象，以及 `null` 和 `undefined` —— 天啊！我可能在代码中用到了它们，但是它们却不存在于我的代码之中。

> 在我的 JavaScript 宇宙里，值漂浮在天空之上。

![image](https://user-images.githubusercontent.com/17036920/110733591-335b6b80-8261-11eb-9675-50f4fdef0826.png)

“等等”，你可能会说，“我通常都在我的代码中考虑这些值。”在这，我们可能要稍微跳脱一点，这个思维模式还需要预先了解一些其他东西。[Give it five minutes](https://click.convertkit-mail.com/p9uw3k6m2riqu9px9nur/58hvh8uokpzq75u6/aHR0cHM6Ly9zaWduYWx2bm9pc2UuY29tL3Bvc3RzLzMxMjQtZ2l2ZS1pdC1maXZlLW1pbnV0ZXM=)

回到值。粗略地来说，它们有两种类型。

### 原始值
`原始值`包括数字和字符串等。打开你的浏览器的控制台，使用 `console.log()` 方法打印出这些原始值

```javascript
console.log(2);
console.log("hello");
console.log(undefined);
```

所有的原始值通常都有一些内容。***在我的代码中没有任何方法可以影响它们***。这听起来有一些模糊，所以接下来我会把它解释的更明确。但现在，我会说这些原始值就像星星 —— 寒冷并且遥远，但是在我们需要的时候，它总在那里。

> 这是第一种值

## 对象和函数
**对象和函数**也是值，但它们不是原始值，这非常特别。继续在浏览器的控制台里打印它们:

```javascript
console.log({});
console.log([]);
console.log(x => x * 2);
```

注意浏览器的控制台在显示它们的时候和原始值有什么不同。有一些浏览器可能会在之前显示一个箭头，并在你点击的时候做一些事情.如果你安装了一些不同的浏览器（比如 Chrome 和 Firefox），比较一下对象和函数看起来有什么不同。

对象和函数致所有特别，是因为**我可以在我的代码里操作它们**。举个例子，我可以将它们链接到其他的值。这有些模糊 —— 所以我们在之后会重新聊这个问题。现在，我可以说如果原始值是星星的化，函数和对象更像漂浮在我的代码附近的岩石。它们离我足够近，我可以操作它们。

> 这是第二种值

你可能会有些问题。很好，如果你发问了，JavaScript 宇宙会回答的！当然，你得知道如何去发问。

### 表达式

有许多问题是 JavaScript 回答不了的。如果你想知道是应该坦诚地告诉你的朋友你的真实感受，还是应该永久隐瞒，JavaScript 恐怕就帮不上忙了。

但是有一些问题 JavaScript 会非常乐于回答。这些问题有一个特殊的名字 —— 表达式。

如果你“问”表达式 `2 + 2`，JavaScript 会“回答” `4`。

```javascript
console.log(2 + 2); // 4
```

表达式就是 JavaScript 能回答的问题。JavaScript 只通过一种我们知道的方式来回答表达式 —— 值。

![image](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1578681449/just-javascript-email-images/jj02/expression.gif)

如果“表达式”这个词有些困扰你，可以把它想象成***表达***了一个值的一段代码。你可能会听见人们说 `2 + 2` “的结果” 或者 “计算成” `4`。这些都是对同一事物的不同说法。

我们问了 JavaScript `2 + 2`，它回答 `4`。**表达式的结果永远都是一个值。**现在我们会了解到表达式会变得多么危险！

我之前说过 JavaScript 的值会有许多类型：数字，字符串，对象等等。我们如何知道这些值的类型呢？

> 这听起来是个问题，我们会确定会问这个问题吗？

## 检查类型
首先，所有的值在 JavaScript 的宇宙里看起来都一样 —— 天空中的亮点。但是如果你仔细看，你会认识到不超过十种类型的值。同类型的值的行为是差不多的。

如果我们想要检查一个值的类型，我们可以用 `typeof` 操作符。JavaScript 将会用一个预定的字符串值来回答，比如 `"number"`，`string` 或者 `"object"`.

![image](https://user-images.githubusercontent.com/17036920/110740547-327d0680-826e-11eb-8ce5-dcc0e1cd53b1.png)

你可以在浏览器控制台里试试下面的例子：

```javascript
console.log(typeof(2)); // "number"
console.log(typeof("hello")); // "string"
console.log(typeof(undefined)); // "undefined"
```

在这，`typeof(2)` 是一个表达式 —— 它的结果是 `"number"` 字符串。

严格来说，`typeof` 不需要括号。举个例子，`typeof 2` 和 `typeof(2)` 的效果是一样的。然而，有时候括号会避免一些不清楚的地方。下面的例子中，有一个在去掉括号后会出问题。猜猜是哪个？

```javascript
console.log(typeof({})); // "object"
console.log(typeof([])); // "object"
console.log(typeof(x => x * 2)); // "function"
```

你可以在浏览器的控制台里验证你的猜想。

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1578948458/just-javascript-email-images/jj02/typeof.gif)

现在再看看上面三个例子 —— 这次更仔细一些关注结果。你找到了意料之外的结果吗？为什么？

## 值的类型

作为有抱负的天文学家，你可能想要知道在 JavaScript 天空中所有的值的类型。在接近 25 年的 JavaScript 研究历史中，科学家们仅仅发现了这些类型：

### 原始类型值：

- 未定义（undefined）用于预期外缺失的值
- 空（null）用于预期之中缺失的值
- 布尔（true 和 false）用于逻辑运算
- 数字（-100, 3.14 等等）用于数学计算
- 字符串（"hello", "abracadabra" 等等）用于文本
- Symbols(并不常用)用于隐藏实现细节
- 大整数（新的并且不常用）用于数学中很大的数字

### 对象和函数

- 对象（{} 等等）用于一组相关的数据或代码
- 函数（x => x * 2 等等）用于引用代码

## 没有其他类型

你可能会问：“但不是还有其他的类型吗？我用过的，比如数组？”

在 JavaScript 中，除了我们刚刚列举的基本值的类型外，再没有其他的类型了。剩下的都是对象！举个例子，甚至数组，日期以及正则表达式在 JavaScript 中都是对象！

```javascript
console.log(typeof([])); // "object"
console.log(typeof(new Date())); // "object"
console.log(typeof(/(hello|goodbye)/)); // "object"
```

你可能会说：“我知道了，这是因为所有东西都是对象！”，哈哈，这是个广为流传的传说，但并不正确。尽管代码 `"hi".toUpperCase()` 使 `"hi"` 看起来像个对象，但它不过是一种幻觉。JavaScript 在你这么做的时候创建了一层外部对象，并在完成操作后立即丢弃了它。

如果这个机制你还没有完全了解也没关系。**现在，你只需要记住例如数字或者字符串等原始值，它们不是对象。**

## 回顾

让我们回顾一下目前所学：

1.  **除开值，还有其他的东西** 。我们可以想象值就像漂浮在 JavaScript 宇宙中不同的东西。它们不存在我们的代码***内部***，但是我们能通过代码引用到它们。
2. **值有两种分类，原始值，以及对象和函数。** 整体来看，总共有 9 个不同的类型。每个类型都有不同的目的，但有一些很少用到
3. **有一些值是单独的。** 举个例子，`null` 是空类型唯一的值，`undefined` 也是未定义类型唯一的值。在接下来的学习中，这两个单独值经常会惹一些麻烦！
4. **我们可以通过表达式来问问题。** JavaScript 总是会用值来回答我们。举个例子，`2 + 2` 表达式的答案是 `4`。
5. **我们可以 `typeof` 表达式来检测类型。** 举个例子，`typeof(4)` 是一个字符串值 `number`。

## 练习
[练习题](https://click.convertkit-mail.com/p9uw3k6m2riqu9px9nur/vqh3hmu3e2dlgztg/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL1BMeVRLQj9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)
