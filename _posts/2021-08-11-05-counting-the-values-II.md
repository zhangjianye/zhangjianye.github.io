---
layout: post
title: 05.Counting the values II
date: 2021-08-11
tags: JustJavascript
---

> from https://justjavascript.com/

在接着往下之前，让我们先回顾一下我们在 JavaScript 宇宙里的旅程。

![image](https://user-images.githubusercontent.com/17036920/111931215-b4362500-8af5-11eb-99ac-31dad9281801.png)

在之前的模块中，我们看到了未定义、空值、布尔值和数字类型的值。我们接下来会“数一数”剩下的值 ——  从大整数开始吧。

## 大整数

![image](https://user-images.githubusercontent.com/17036920/111931295-e47dc380-8af5-11eb-82b4-95e1a10fb696.png)

大整数最近才刚刚被加入到 JavaScript 中，所以你可能并没有看到它们的广泛应用。如果你使用的是老版本浏览器，它们也不会工作。常规的数字不能准确地去表示特别大的证书，而大整数正是为了[弥补这个问题](https://click.convertkit-mail.com/75u03gkn48f2uok8q2s9/qvh8h8u2p5lkl5al/aHR0cHM6Ly92OC5kZXYvZmVhdHVyZXMvYmlnaW50)

```js
let alot = 9007199254740991n; // Notice n at the end
console.log(alot + 1n); // 9007199254740992n
console.log(alot + 2n); // 9007199254740993n
console.log(alot + 3n); // 9007199254740994n
console.log(alot + 4n); // 9007199254740995n
console.log(alot + 5n); // 9007199254740996n
```

在商业中四舍五入可不好！在金融计算中，精准度尤为重要。注意任何事情都是有代价的。操作真正地大数字会耗费更多的时间和资源。

在我们的宇宙中有多少大证书呢？规范上说大数字可以达到任意精度。这意味着**在我们的 JavaScript 宇宙中，有无穷多个大整数 —— 对应着数学中的每个整数。**

耶...

如果这听起来很奇怪，考虑下在数学中无穷的整数，这会熟悉些。（如果没有，就再想一下）。从“数学世界”到“JavaScript 世界”并不遥远。

当然，在实践中，我们不可能在计算机内存中存下所有的大整数。如果我们这样去做，很可能会崩溃或者被冻结。但是从概念上，数数爵士将会无穷无尽地去数每个大整数了。

## 字符串

![image](https://user-images.githubusercontent.com/17036920/111932025-7cc87800-8af7-11eb-831d-3d38dd824e91.png)

字符串表示 JavaScript 中的文本。有三种方式写下字符串（单引号，双引号，反引号），但结果是一样的。

```js
console.log(typeof("こんにちは")); // "string"
console.log(typeof('こんにちは')); // "string"
console.log(typeof(`こんにちは`)); // "string"
```

空字符串也一样：

```js
console.log(typeof('')); // "string"
```

### 字符串不是对象

所有的字符串都有些内置属性。

```js
let cat = 'Cheshire';
console.log(cat.length); // 8
console.log(cat[0]); // "C"
console.log(cat[1]); // "h"
```

但这并不意味着字符串是对象！字符串属性的选取方式和对象不同。举个例子，你不能给 `cat[0]` 去赋值。字符串是原始类型，而所有的原始类型都是不可变的。

### 每个可能的字符串的值

**在我们的宇宙里，每个可能的字符串都有个清楚地值。** 是的，它们包括你的祖母的名字，或者你十年前发表的一篇文章，以及还没写出来的 Matrix 5 的脚本。

当然，也不是所有的字符串都能塞到计算机内存里。但所有字符串的可能会塞到你的脑子里。我们的 JavaScript 宇宙是对于人的，不是计算机！

这可能带来一个问题，这段代码创建了一个字符串吗？

```js
// Try it in your console
let answer = prompt('Enter your name');
console.log(answer); // ?
```

还是说它只是在我们的宇宙中提供了一个已经存在的字符串？

回答这个问题取决于我们学习 JavaScript 的方向是“从外部”还是“从内部”的。

外部思维模型的话，答案会基于某种具体的实现。每个字符串表示了一块内存，或几块内存，或一条[绳子](https://click.convertkit-mail.com/75u03gkn48f2uok8q2s9/9qhzhdu3rmee07b9/aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvUm9wZV8oZGF0YV9zdHJ1Y3R1cmUp)，在 JavaScript 引擎中表现出来。

但是在我们的内部思维模式，这个问题毫无意义。在我们的宇宙中，我们不会说字符串是“被创造”或者“被提供”。

为了保持我们的思维模式简单，我们会说**从一开始所有的可能字符串就已经存在了 —— 每个字符串都有一个值。**

## Symbols

Symbols 也是最近才加到了语言里。

```js
let alohomora = Symbol();
console.log(typeof(alohomora)); // "symbol"
```

对于它，如果没有对于对象很深的了解的话，比较难以解释它的属性和行为，所以暂时我们会跳过它。对不起啊 symbols !

![image](https://user-images.githubusercontent.com/17036920/111949877-6e408780-8b1c-11eb-9b28-da1630fe05e3.png)

## 对象

![image](https://user-images.githubusercontent.com/17036920/111949891-75679580-8b1c-11eb-84a7-c8a361863443.png)

最后，我们来到了对象

这包括了数组，日期，正则以及所有其他不适原始类型的值：

```js
console.log(typeof({})); // "object"
console.log(typeof([])); // "object"
console.log(typeof(new Date())); // "object"
console.log(typeof(/\d+/)); // "object"
console.log(typeof(Math)); // "object"
```

和之前的一切不同，对象不适一个原始类型值。这意味着在默认情况下，它们是可变的。我们可以用 `.` 或者 `[]` 来访问它们的属性：

```js
let rapper = { name: 'Malicious' };
rapper.name = 'Malice'; // Dot notation
rapper['name'] = 'No Malice'; // Bracket notation
```

我们还没有细致地讨论过属性，所以你的思维模式可能还有些模糊。在之后我们会回来讨论它们。

### 创建一个自己的对象

在对象里有一件可以让数数爵士非常兴奋的事情。**我们可以创建它们，我们可以创建自己的对象！**

在我们的思维模式中，已经讨论过了的所有的原始类型值 —— 空值、未定义、布尔值、数字和字符串 —— 都是“已经存在”的。我们不能“制造”一个新的字符串或者数字，我们只能“提供”值：

```js
let sisters = 3;
let musketeers = 3;
```

![image](https://user-images.githubusercontent.com/17036920/111950374-25d59980-8b1d-11eb-9e44-857d5324fea6.png)

而对象的不同在于我们可以创造更多。**每次我们使用 {} 的对象字符，我们都创建了一个新的对象值：**

```js
let shrek = {};
let donkey = {};
```

![image](https://user-images.githubusercontent.com/17036920/111950487-4d2c6680-8b1d-11eb-9bc9-1696c5df289e.png)

这些对于数组，日期以及其他的对象都是成立的。举个例子，通过字面 `[]` 来创建一个新的数组值 —— 这个值之前从没存在过。

### 对象消失了吗？

你可能会奇怪：如果对象不消失，它们会永远存在吗？JavaScript 的设计使得我们无法从代码里分辨出不同的方式。举个例子，我们不能销毁一个对象：

```js
let junk = {};
junk = null; // Doesn't necessarily destroy an object
```

取而代之，JavaScript 会自动进行垃圾回收。

这意味着尽管我们不能销毁对象，它们也可能会“消失”，如果在我们的代码中没有任何方式可以触达它们的话:

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/garbagecollection-optim.gif)

JavaScript 不会保证什么时候触发垃圾回收机制。

除非你想要去找出为什么你的 app 占用了太多的内存，你都不需要去考虑垃圾回收机制。我只是为了告诉你，我们可以创建对象 —— 但我们不能销毁对象。

在我的宇宙里，对象和函数离我的代码最近。这提醒我可以随时操作或创建它们。

## 函数

![image](https://user-images.githubusercontent.com/17036920/111951180-43efc980-8b1e-11eb-9ab9-72b0fde182d0.png)

将函数从代码中分离出来作为值来考虑，会有些奇怪。它们按理说应该是我们的代码，或者不是？

### 函数也是值

我们定义了一个函数，所以我们可以在代码中调用它们。然而，真正地理解 JavaScript 中的函数，你需要忘记关于 ***为什么*** 它们可以复用。取而代之，我们会如同其他的值一样来考虑函数：数字，对象，函数。

为了了解函数，我们将它们和数字与对象做个比较。

首先，考虑 `for` 循环中运行 `console.log(2)` 7次：

```js
for (let i = 0; i < 7; i++) {
  console.log(2);
}
```

**有多少个不同的值被传入了 console.log?** 为了回答这个，让我们回忆下我们写下的`2`这个值得意思。这是个数字字符量。一个字符量是一个表达式 —— 对于我们宇宙的一个问题。我们的宇宙中每个数字只有一个值，所以“回答”我们的问题的是“提供了”数字2这个答案。**所以答案是一个值。** 我们可以看见打印了7次 —— 但是我们每次都传了相同的值。

快速看一下对象。

这个 `for` 循环运行了7次 `console.log({})`

```js
for (let i = 0; i < 7; i++) {
  console.log({});
}
```

**现在一共传了几次不同的值到 console.log?** 同样，`{}`是个字符量 —— 是个对象字符量。我们刚学了，JavaScript 宇宙“回答”对象字符量不是提供任何东西。而是，创建了一个新的对象值 —— 作为 `{}` 对象字符量的结果。**所以上面的代码创建了7个不同的对象值，并答应了出来。**

让我们更深入一些。

现在看看函数

```js
for (let i = 0; i < 7; i++) {
  console.log(function() {});
}
```
**console.log 被传入了多少个不同的值？**

### 等等

在你没回答之前，别往下翻

...

...

...

...

...

...

...

...

...

...

答案是 7 个。

**每次我们执行的代码里有一个函数表达式，一个新的函数值就会出现在我们的宇宙里。**

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1581382911/just-javascript-email-images/jj05/function-creation-optim-v2.gif)

同样，`function () {}` 是一个表达式。和其他表达式一样，函数表达式也是一个在 JavaScript 宇宙中的问题 —— **答案就是创建了一个新的函数。** 这和用 `{}` 创建对象很类似。函数和对象很类似！

从技术上，在 JavaScript 中函数也是一个对象。我们之所以区分它们，是因为它有很多与一般对象不一样的特性。但是，笼统来说，如果我们可以在对象上做什么事，同样在函数上也是可以的。它们是非常特殊的对象。

### 调用函数

这段代码会打印什么？

```js
let countDwarves = function() { return 7; };
let dwarves = countDwarves;
console.log(dwarves);
```

如果你没有仔细看得话，你可能会觉得是打印 `7`。

现在在控制台里试一下！真实的结果会根据浏览器不同而不同，但是你不会看到数字7，而是函数本身。

如果你跟上了我们的思维模式，这些行为就是合理的了：

1. 首先，我们通过 `function() {}` 表达式创建了一个函数，然后将 `countDwarves` 变量指向了它。
2. 接着，我们将 `dwarves` 变量指向了 `countDwarves` 的值 —— 同样的函数值
3. 最后，打印出 `dwarves` 变量指向的值。

我们没有任何地方调用了这个函数！

作为结果，`countDwarves` 和 `dwarves` 指向了同一个值，都是函数。所以，函数是一个值。我们可以用变量指向它们，就和数字，对象这些一样。

**当然，如果我们想调用函数，我们可以这样：**

```js
let countDwarves = function() { return 7; };
let dwarves = countDwarves(); // () is a function call
console.log(dwarves);
```

注意 `let` 和 `=` 都没有调用函数，`()` 才执行了函数调用 —— 而且只有它可以!

**加上 `()` 会改变函数的意义：**

- `let dwarves = countDwarves` 表示“将 `dwarves` 指向 `countDwarves` 指向的值”
- `let dwarves = countDwarvew()` 表示“将 `dwarves` 指向函数 `countDwarves` **返回** 的值。”

事实上，`countDwarves()` 也是个表达式。叫做调用表达式。“回答”调用表达式，JavaScript 会运行函数内的代码，然后将返回值作为结果交给我们。（在例子里，是7）

我们在以后还会看到函数调用的更多细节。

## 回顾

多么愉快的旅程！在上两块里，我们看到了 JavaScript 的每个类型的值。让我们通过数数爵士来会议看看究竟有多少类型吧，从原始类型开始：

![image](https://user-images.githubusercontent.com/17036920/111953803-1442c080-8b22-11eb-8d21-dcf823b18e61.png)

- 未定义： 只有一个值 `undefined`
- 空值： 只有一个值 `null`
- 布尔，有两个值 `true` 和 `false`
- 数字： 每个[浮点数](https://click.convertkit-mail.com/75u03gkn48f2uok8q2s9/m2h7h6u0zplx59sm/aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvRG91YmxlLXByZWNpc2lvbl9mbG9hdGluZy1wb2ludF9mb3JtYXQ=)对应一个值
- 大整数：每个可能的整数都有一个值
- 字符串：每个可能的字符串都有一个值
- Symbols: 我们跳过了 Symbols, 之后再讨论它！

还有两个特殊的类型，是因为它们可以创建自己的值：

![image](https://user-images.githubusercontent.com/17036920/111954015-713e7680-8b22-11eb-84a7-8be04c991726.png)

- 对象：每个对象字面量都会创建一个值
- 函数：每个函数表达式都会创建一个值

观察 JavaScript 中不同的”天体“非常有趣。目前我们已经了解了所有的值，并且了解了它们之间的不同。**举个例子，写下 2 或者 ”hello“ 总是”提供“了同样的数字或字符串值。但是 {} 或者 function() {} 总是会创建新的，不同的值。** 这个观点在对于理解在之后的 JavaScript 主题至关重要。

## 练习
[练习题](https://click.convertkit-mail.com/75u03gkn48f2uok8q2s9/08hwhguwr5p4l7ul/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL1NURWVNeT9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)



















