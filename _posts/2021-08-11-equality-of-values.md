---
layout: post
title: Equality of values
date: 2021-08-11
tags: JustJavascript
---

> from https://justjavascript.com/

是时候讨论一下 JavaScript 的相等了！我会告诉你为什么这很重要。

想象一下我们在蒙面嘉年华上洽谈业务交易。你会跟两个人交谈，却无法意识到你是不是跟同一个人交谈了两次。又或者你可能会认为跟你交谈的是同一个人，但其实是不同的两个人！

![image](https://user-images.githubusercontent.com/17036920/113999975-21cfa880-988d-11eb-895c-87dfb7217a4f.png)

**如果你对于 JavaScript 的相等模型了解的不是很清楚，那每天就都像是一场蒙面舞会 —— 这可不是一个好主意。** 你用于不会十分确定你是否在处理同样的值，还是两个不同的值。最后的结果就是，你会犯错 —— 比如说改变了你笨不想改变的值。

幸运的是，我们已经对了解 JavaScript 中相等的概念做了很多功课。它会很自然地进入到我们的思维模式中。

## 相等的种类

在 JavaScript 中，有几种相等的方式。如果你写过一阵 JavaScript，你可能会对以下至少两种方式比较熟悉：

- **严格相等:** a === b (三个等号)
- - **不严格相等:** a == b (量个等号)
- - **同值相等:** Object.is(a, b)

许多教程里都根本不会提到 ***同值相等。*** 我们不走寻常路，就从它开始解释吧。接着我们就能用它去解释其他的种类了：

### 同值相等： Object.is(a, b)

在 JavaScript 中， `Object.is(a, b)` 告诉我们 `a` 和 `b` 是否有相同的值：

```js
console.log(Object.is(2, 2)); // true
console.log(Object.is({}, {})); // false
```

这就叫 **同值相等。**

事实上，在我们的思维模式里，什么是”同值“呢？。你可能从直觉上已经有了解了，但是还是让我们验证一下。

### 检验你的直觉

考虑下面这个例子：

```js
let dwarves = 7;
let continents = '7';
let worldWonders = 3 + 4;
```

就跟我们了解的一样，对于这个代码片段的草图会像这样：

![image](https://user-images.githubusercontent.com/17036920/115334251-9ed41980-a1cd-11eb-90f2-cfafc3556bd3.png)

现在试着用**上面的图**去回答下面的问题：

```js
console.log(Object.is(dwarves, continents)); // ?
console.log(Object.is(continents, worldWonders)); // ?
console.log(Object.is(worldWonders, dwarves)); // ?
```

写下你的答案，并且想想你该如何解释

### 占位

在完成之前不要滚动下来...

...

....

...

...

...

这不是一个大问题！这里是答案：

1. `Object.is(dwarves, continents)` 是返回 `false` 值，因为 `dwarves` 和 `continents` 是不同的值。
2. `Object.is(continents, worldWonders)` 是 `false`，它们也是不同的值。
3. `Object.is(worldWonders, dwarves)` 是 `true`，它们是同一个值。

如果两个值在我们的图中用同一个形状来表示，那意味着它们并不真正是两个不同的值。它们是同一个值！这时候 `Object.is(a,b)` 就会返回 `true`。

在前面的模块里，我们“数”了所有的值。但事实上，我们是学习了是什么造成了值与值之间的区分。因此，我们同样也学习了它的反面 —— 什么意味着值是同一个。

如果你对这个观点还很困惑的话，你可以回看之前的章节，并且重新做一遍[练习题](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/p8hehqu5px3dz4hq/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL1NURWVNeT9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)。我保证这是合理的!

### 但关于对象呢？

在这个观点下，你可能会对对象感到忧虑。你可能听说过相等性在对象里不起作用，或者说它们比较的是“引用”。 **如果你仍然有这样的直觉，请暂时将它们完全抛开。**

取而代之，看看下面的代码片段：

```js
let banana = {};
let cherry = banana;
let chocolate = cherry;
cherry = {};
```

打开你的笔记本或者可以话草稿的 app, 画下这些变量和值的图。这有些困难，因此你最好一步一步地去画。

记住，`{}` 永远意味着“创建一个新的对象值”。同样记住 `=` 意味着“将左边的线连接到右边的值”。

**在你画完之后，** 写下你的答案：

```js
console.log(Object.is(banana, cherry)); // ?
console.log(Object.is(cherry, chocolate)); // ?
console.log(Object.is(chocolate, banana)); // ?
```

确保你用图画来回答了问题。

### 占位

在完成之前不要滚动下来...

...

....

...

...

...

你画图应该是如下的步骤

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1582119851/just-javascript-email-images/jj06/banana-anim-final.gif)

1. `let banana = {}`
  - 声明 banana 变量
  - 创建了一个新的对象值 {}
  - 将 banana 变量连接到它 
2. `let cherry = banana`
  - 声明 cherry 变量
  - 将 cherry 变量连接到 banana 变量连接到的地方
3. `let chocolate = cherry`
  - 声明了 chocolate 变量
  - 将 chocolate 变量连接到 cherry 变量连接到的地方
4. `cherry = {}`
  - 创建一个新的对象值 {}
  - 将 cherry 变量连接到它

完成了所有步骤后，你应该得到如下的图：

![image](https://user-images.githubusercontent.com/17036920/115335500-ec518600-a1cf-11eb-8040-405dc150c0c7.png)

现在来看看答案:

1. `Object.is(banana, cherry)` 是 `false`， 它们连接到了不同的值。
2. `Object.is(cherry, chocolate)` 是 `false`，它们也连接了不同的值。
3. `Object.is(chocolate, banana)` 是 `true`， 它们连接了同一个值。

如你所见，我们没有在对象是否相等中添加如何额外的概念。它已经在我们的思维模式中了。

这就是我们需要了解的所有信息！

### 严格相等：a === b

你可能在以前用过**严格相等**操作符：

```js
console.log(2 === 2); // true
console.log({} === {}); // false
```

还有个对应的反向操作符 `!==` 。

### 同值相等 vs 严格相等

所以 `Object.is` 和 `===` 之间到底有啥区别呢?

同值相等 —— `Object.is(a, b)` —— 在我们的思维模式中有明确的意义。它在我们的宇宙中代表“同一个值”。

在几乎所有的情况中，同样的直觉对于严格相等是一致的。举个例子， `2 === 2` 的值是 `true`， 因为 `2` 总是“表示”同一个值：

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1582304092/just-javascript-email-images/jj06/equality_small.gif)

反过来， `{} === {}` 是 `false` 的原因是因为每个 `{}` 创建了不同的值：

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1582304092/just-javascript-email-images/jj06/inequality_small.gif)

在上面的例子中， `a === b` 与 `Object.is(a, b)` 有相同的表现。然而，有两个例外：

**以下情况是这个规则的例外** —— 就如同你在学习英语时得去记住一些不规则动词一样。所有的特殊情况都涵盖在了我们之前讨论的 “特殊数字” 中：

1. `NaN === NaN` 是 `false`， 尽管它们是同一个值。
2. `-0 === 0` 和 `0 === -0` 是 `true`， 尽管它们是不同的值。

尽管这两种情况很少见，我们还是仔细研究一下它们。

### 第一个特殊案例：NaN

在我们之前的 ***数一数每个值*** 的章节中，`NaN` 是一个特殊的数字，当你做了类似 `0 / 0` 这类无效的运算的时候就会出现：

```js
let width = 0 / 0; //NaN
```

如果你接着用 `NaN` 来计算的话，会再次得到 `NaN`:

```js
let height = wiedth * 2; //NaN
```

你可能不会故意这么做，但它可能会在你处理一开始就有错的数据的情况下，或者说你的计算有错误的情况下发生。

**记住 `NaN === NaN` 永远是 `false`**

```js
console.log(width === height); //false
```

然而， `NaN` 和 `NaN` 是同一个值：

```js
console.log(Object.is(width, height)); //true
```

![image](https://user-images.githubusercontent.com/17036920/115490598-fab3a680-a290-11eb-973d-6336dcb800b0.png)

这真是让人困惑。

关于为什么 `NaN === NaN` 会是 `false` 涉及到一个很久远的历史原因，所以我建议你还是就默默接受吧。你可能想判断你的代码中的值是不是 `NaN`（比如打印一个警告）。

```js
function resizeImage(size) {
  if (size === NaN) {
    // Doesn't work: the check is always false!
    console.log('Something is wrong.');
  }
  // ...
}
```

取而代之，有些其他的判断方法：

- `Number.isNaN(size)`
- `Object.is(size, NaN)`
- `size !== size`

最后一条可能会有些意外。冷静一下。如果你还是不知道如何检测 `NaN`， 试着重新读一遍这一节，然后再想想。

(在最后会有答案)

### 第二个特殊情况：-0

在常规的数学中，并没有”负0“的概念，但是因为[一些原因](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/48hvh7uq7g59rxfx/aHR0cHM6Ly9zb2Z0d2FyZWVuZ2luZWVyaW5nLnN0YWNrZXhjaGFuZ2UuY29tL2EvMjgwNzA4)，在浮点运算中它是存在的。对于它，有些有趣的情况。

**对于 `0 === -0` 和 `-0 === 0` 都是 `true`**

```js
let width = 0; // 0
let height = -width; // -0
console.log(width === height); // true
```

然而，`0` 和 `-0` 是不同的值：

```js
console.log(Object.is(width, height)); // false
```

![image](https://user-images.githubusercontent.com/17036920/115491179-18cdd680-a292-11eb-94eb-f20c17454e0c.png)

这也同样让人感到困惑。

实践中，在我整个职业生涯中，还没有遇到过这个问题很重要的情况。

### 代码练习

现在你知道了 `Object.is` 和 `===` 是如何工作的了，我会给你一个小的代码练习。你不一定非要完成它，但是它是一个很有趣的脑筋急转弯。

**写一个名为 strictEquals(a, b) 的函数，它的返回应该和 a===b 一样。你的实现必须不包括 ==== 或者 !== 操作符。**

这里是[我的答案](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/08hwhguwpzoxd8sl/aHR0cHM6Ly9naXN0LmdpdGh1Yi5jb20vZ2FlYXJvbi8wOGE4NWEzM2UzZDA4ZjNmMmNhMjVmYjE3YmQ5ZDYzOA==)，如果你想对照检验一下自己的答案的话可以看看。这个函数当然没啥用，但是会帮助我们理解 ```===```。

### 别怕

了解这些特殊数字的概念及行为会让人有些压力。不要对这些特殊案例感到有压力。

它们并不寻常。现在你知道了它们的存在，你会在实践中认出它们。在大多数的情况里，我们关于”同样的值“的直觉对于 `Object.is(a, b)` 和 `a === b` 这两种情况都适用。

## 宽松相等

最后，我们讨论一下最后一种相等。

**宽松相等（两个等号）** 是 JavaScript 中的一朵奇葩。

给你一些让人抓狂的例子吧：

```js
console.log([[]] == ''); // true
console.log(true == [1]); // true
console.log(false == [0]); // true
```

[等等，这是啥](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/vqh3hmu3qgx4oxug/aHR0cHM6Ly9kb3JleS5naXRodWIuaW8vSmF2YVNjcmlwdC1FcXVhbGl0eS1UYWJsZS8=)

关于 **宽松相等（也叫”抽象相等“）** 的规则非常的诡异和让人困惑。它们被广泛的认为是早期的不良设计导致的。甚至许多编码标准禁止在代码中使用 `==` 和 `!=`。

尽管我们的教程对此没有强烈的倾向，我们也不会在现在过多地讨论 **宽松相等** 。它在现在的代码库里并不寻常，并且它的规则在语言中并不是非常重要 —— 或者说在我们的思维模式中。如果你感到好奇，你可以在这里看看[它是怎么工作的。](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/m2h7h6u0lrlv74cm/aHR0cHM6Ly9kZXZlbG9wZXIubW96aWxsYS5vcmcvZW4tVVMvZG9jcy9XZWIvSmF2YVNjcmlwdC9FcXVhbGl0eV9jb21wYXJpc29uc19hbmRfc2FtZW5lc3MjTG9vc2VfZXF1YWxpdHlfdXNpbmc=)但是没必要去记住它。你需要留点”内存“来记别的事情！

这有一个值得了解并相对应用的比较广泛的案例：

```js
if (x == null) {
  // ...
}
```

这段代码等于下面这段：

```js
if (x === null || x === undefined) {
  // ...
}
```

然而，尽管使用 `==` 会在一些团队中有些便利。但是最好现在团队中讨论你们的代码库中在哪些情况允许 `==`。

## 回顾

- JavaScript 有几种相等的方式。包括**同值相等** ， **严格相等**  和 **宽松相等** 。
- **同值相等** 或者说 `Object.is(a, b)`， 根据我们之前提到的概念，比较了两个值是否相同
  -  了解相等的不同种类可以帮助你预防 bug ！你经常会需要知道如何对待相同的值和不同的值
  -  当你画下值和变量的图示时，相同的值不能出现两次。`Object.is(a, b)` 在变量 `a` 和 `b` 在我们的图中指向同一个值得时候返回 `true`。
  -  **同值相等** 是最容易解释的，这也是为什么我们从它开始。然而，它在写法上有些繁琐。
- 实践中，你经常会用到 **严格向德国** ， 或者说 `a === b`，大多数情况，它和 **同值相等** 的表现一样，除了两个特殊案例：
  -  `NaN === NaN` 返回 `false`， 尽管它们是同一个值
  -  `0 === -0` 和 `-0 === 0` 返回 `true`， 尽管它们是不同的值。
-  你可以使用 `Number.isNaN(x)` 来判断 `x` 的值是不是 `NaN`。
-  **宽松相等（==）** 有一系列奇葩的规则，它通常应该被避免。

最后，你可能仍然会对 `size !== size` 可以判断 `size` 的值是不是 `NaN` 感到奇怪。我们说过，会在最后看看这个问题。它可以起作用的原因是我们刚学过的 `NaN === NaN` 是 `false`。所以反向的（`NaN !== NaN`) 就是 `true`。因为 `NaN` 是唯一一个不等于它自己的值，所以 `size !== size` 就表示 `size` 是 `NaN` 了。

事实上，当初之所以设计 `NaN === NaN` 返回 `false` 的一个原因就是确保可以检测到 `NaN`！这个在 JavaScript 存在之前就这么决定了。这纯粹是个历史原因，但是很有趣。

## 练习
[练习题](https://click.convertkit-mail.com/n4ud8kp9r0iqu358m3i0/dphehmuw254kewim/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL3dwUUtJND9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)


































































