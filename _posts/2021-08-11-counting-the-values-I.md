layout: post
title: Counting the values I
date: 2021-08-11
tags: JustJavascript
---

> from https://justjavascript.com/


在这一节，我们将会更近距离地观察 JavaScript 世界中的值。但在这之前，我们需要解决掉房间里的一头“大象”。`JavaScript` 世界真的存在吗？

## 模拟 JavaScript

我生活在 JavaScript 宇宙中的一颗小行星上。

当我问 JavaScript 世界一个问题，它会用一个值来回答我。我当然不会提出所有的值。变量，导线，值 —— 它们共同充满了我的世界。在我周围的 JavaScript 世界对我来说如此真实 —— 就像你生活的真实环境一样。

但有时候，在写出下一行代码的时候，会有片刻的寂静。一个在下一个函数调用之前的空闲时刻。一个矩阵中的小小问题。在这些时刻，我会看见一个比我感受到的更大的世界。

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/dream-glitch-optim.gif)

在这个呈现在我眼前的世界中，没有变量和值。没有表达式也没有字符。取而代之，这里有夸克，有原子，电子，水以及生命等等。也许，你可能对这个世界更熟悉？

在那里，一种被称为“人类”的智慧生物，使用了一个被称为“计算机”的机器来模拟除了***我的*** JavaScript 宇宙。有些人用它来娱乐。有些人用它来赚钱。有些人甚至不需要理由。随着他们的一时兴起，数以千计的“世界”会出生或死亡。

***也许在这之后我的 JavaScript 世界就不那么真实了***

这意味着我们有两个方法来学习它。

### 从外部学习

一个学习我的 JavaScript 世界的方法就是***从外部来学习它。***

也许，你可能会去关注如何模拟出一个我的世界 —— 一个 JavaScript 引擎 —— 让它“真正”的工作。举个例子，你可能会学习到，文本中的一个字符串 —— 我的世界中的一个值 —— 是存储在硅芯片上的一串连续字节。

这样会把我们的思维关注于拥有人类和计算机的真实世界。一些教程会去达到这个目标。但我们的目标却不是这样。

### 从内部学习

我们会从内部来学习 JavaScript 世界。在我之后，将你的思维也转换到 JavaScript 宇宙中来。我们会观察它的定律并进行试验，就如同物理学家在物理世界里做的那样。

**我们会学习 JavaScript 世界究竟是怎样的 —— 而并不考虑它如何实现的。这就如同物理学家可以在不知道一个星星的***物理世界***是否真实的情况下去谈论它的属性。这不重要！我们可以用自己的术语来描述它们！**

我们的思维模式并不倾向于去回答类似“一个值在计算机的内存里是如何被表达的？”这个答案始终在改变！事实上，这个问题的答案随着你的[程序运行时](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/x0hph3ud00mw5oi5/aHR0cHM6Ly92OC5kZXYvYmxvZy9yZWFjdC1jbGlmZg==)不断变化。如果你听过一些关于 JavaScript 如何在内存里“真正”表示数字，字符串，或者对象等的简单解释，那它基本是错的。

对于我来说，每个字符串都是一个值。不是一个“指针”，也不是一个“内存地址” —— 就是一个***值***。**在我的宇宙，值就够了。** 不要让“内存单元”或者其他更底层的隐喻来干扰你去建立一个关于 JavaScript 的高层思维模式。它们会拖慢你的进度！

如果你曾经学过更底层的编程语言，将一些类似“传入引用”，“在栈上分配空间”，“写入一个拷贝”的直觉都扔掉。这些关于计算机如何工作的模型通常会让对于一个 JavaScript 程序里会或不会发生的事情更加难以理解。我们会看到一些底层细节，但仅在[真正需要的时候](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/58hvh8uo22wmr8i6/aHR0cHM6Ly93d3cuam9lbG9uc29mdHdhcmUuY29tLzIwMDIvMTEvMTEvdGhlLWxhdy1vZi1sZWFreS1hYnN0cmFjdGlvbnMv)。它们会作为我们思维模式的补充，但不是基础。

**取而代之，我们思维模式的基础就是这个世界里充满了值。** 每个值都有一些内置类型。有一些事原始值，它们是一些不可变的值。变量是我们代码取得名字和“值”之间的“导线”。我们会在这个基础上建造一切。

对于这些奇怪的视角，我并没有过多的去思考它们。我有导线去连接，有问题去问，有函数去调用。就够了！

星星会在我注视它们的时候更明亮。

当我们眨眼的时候，它还在那里吗？

我耸耸肩。

***“这是一个实现的细节”***

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/dream-glitch-meta-optim.gif)

## 数一数每个值

[数数伯爵](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/48hvh7uq883rxzhx/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1lU3VrTXk4RHlmWQ==)是我童年中的偶像。如果你对芝麻街不熟悉，那我告诉你他最爱的时光就是数东西。到现在，数数伯爵会在 JavaScript 中加入我们来对每个值进行计数。

你可能会感到惊讶：***对值计数*** 到底意味着什么？我们并不在一趟算术课上吧？计数的本质是将事物区分开来。你只会说“两个苹果”，当你看到两个不同的苹果时。区分不同的值，是理解 JavaScript 中***相等*** 这个概念的关键 —— 我们在下一个主题里会谈到。

就像 Virgil 指导  Dante 穿过九层地狱一般，数数伯爵将会陪伴我们穿过 JavaScript 的“天体”，来见到不同的值：布尔，数字，字符串等等。就像一次观光旅游一般。

![image](https://user-images.githubusercontent.com/17036920/111253936-fb806980-864e-11eb-88d5-a4267b7b10b3.png)

### 未定义

我们将从未定义类型开始。数数伯爵在知道这个类型只有 `undefined` 这一个值得时候非常开心。

```js
console.log(typeof(undefined)); // "undefined"
```

![image](https://user-images.githubusercontent.com/17036920/111254061-34b8d980-864f-11eb-827e-29a45736ef37.png)

它被称为未定义，所以你可以没有东西在那 —— 但它***是***一个值，而且是非常真实的！就像黑洞一般，`undefined` 脾气暴躁，并且经常制造出麻烦。举个例子，读取以下属性会中断你的程序：

```js
let person = undefined;
console.log(person.mood);  //TypeError!
```

天啊，还好在 JavaScript 的宇宙中只有一个 `undefined`。你可能会惊讶：它存在的意义是什么？在 JavaScript 中，它代表着一个***意外缺失的值。***

你可以在你的代码里直接写 `undefined` —— 就和你写 `2` 或者 `hello` 一样。然而，`undefined` 通常会“自然产生”。它代表着某些 JavaScript 不知道你想要的值是什么的情况。举个例子，如果你忘记给变量赋值，它就会指向 `undefined`：

```js
let bandersnatch;
console.log(bandersnatch); // undefined
```

![image](https://user-images.githubusercontent.com/17036920/111254437-0c7daa80-8650-11eb-83df-4b8eec772699.png)

之后你也可以将它指向其它的值，只要你愿意，你也可以再次将它指向 `undefined`。

不要一直在意它的名称。它会误导你认为 `undefined` 是某种变量的状态等等。“这个变量还没有被定义”。但是这完全是一个错误的思路。事实上，当你试图去读取一个***确实***没有被定义的变量（或者在 `let` 声明之前），你会得到一个报错：

```js
console.log(jabberwocky); // ReferenceError!
let jabberwocky;
```

这和 `undefined` 没有任何关系。

事实上 `undefined` 和 `2` 于 `hello` 一样，都是原始值。

使用它的时候要小心。

### 空值

![image](https://user-images.githubusercontent.com/17036920/111255164-7fd3ec00-8651-11eb-9f45-2ac773f2ba12.png)

你可以将 `null` 想象成 `undefined` 的姐妹。它们的行为非常类似。举个例子，它们在你去访问它们的属性时都会报错：

```js
let mimsy = null;
console.log(mimsy.mood); // TypeError!
```

![image](https://user-images.githubusercontent.com/17036920/111255240-aa25a980-8651-11eb-97cc-fb5aa1fc8ec6.png)

和 `undefined` 类似，**null 也是这个类型的唯一值。** 然而，`null` 是个骗子。在 JavaScript 里有个 [bug](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/x0hph3ud00mwqob5/aHR0cHM6Ly8yYWxpdHkuY29tLzIwMTMvMTAvdHlwZW9mLW51bGwuaHRtbA==)，它被认为是个对象：

```js
console.log(typeof(null)); // "object" (a lie!)
```

你可能会认为这意味着 `null` 是一个对象。不要掉入这个陷阱！它是一个原始值，并且它和对象一定也不像。不幸的是，`typeof(null)` 是一个历史错误，我们不得不一直伴随它。

在实践中，`null` 是被用作***一个预期之中的缺失的值***。为什么要有 `null` 和 `undefined` 两种值呢？这会帮助你区分到底是代码错误（结果可能是 `undefined`）还是有效的缺失值（可能是 `null`）。然而，这只是一个约定，JavaScript 并不强制如何去使用它们。一些人也会尽量避免这两种情况。

我并不怪它们。

### 布尔

![image](https://user-images.githubusercontent.com/17036920/111263325-a51c2680-8660-11eb-8bc9-a035edea9fc8.png)

如同白天和黑夜，**布尔变量有两个值：`true` 和 `false`。**

```js
console.log(typeof(true)); // "boolean"
console.log(typeof(false)); // "boolean"
```

我们可以对它们执行逻辑运算：

```js
let isSad = true;
let isHappy = !isSad; // The opposite
let isFeeling = isSad || isHappy; // Is at least one of them true?
let isConfusing = isSad && isHappy; // Are both true?
```

数数伯爵现在会检查你的思维模式。打开一个[草稿本](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/48hvh7uq883r7zsx/aHR0cHM6Ly93d3cuZXhjYWxpZHJhdy5jb20v)或拿出几张纸，画出上面这段代码中的值，变量和它们之间的导线。

### 等一下

在写完之前别往下翻了

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

对着这个图检查你的答案：

![image](https://user-images.githubusercontent.com/17036920/111263723-4c00c280-8661-11eb-8abe-4cef84f1ffed.png)

首先，确认 `isHappy` 指向的是 `false`，`isFeeling` 指向的是 `true`，以及 `isConfusing` 指向的是 `false`。（如果你得到了不同的答案，那么你在这条路上就犯了些错误，回过头一行一行的检查一下）

接下来，确认 **只有一个 `true` 和 `false` 在你的草稿上。** 数数伯爵说这非常重要！不管这些布尔值是如何存在内存里的，***在我们的思维模式里，就只有它们两个。*** 

## 数字

![image](https://user-images.githubusercontent.com/17036920/111264015-c92c3780-8661-11eb-9b67-36858cb49249.png)

目前为止，我们已经数了4个值：`null`， `undefined`，`true` 和 `false`。

稳住了，因为接下来我们将要添加一大堆诸如18万万亿，437万万亿，736万亿，740亿，4亿5千4百万，82万，600，20 等等等等一大堆值到我们的思维模式中了。

当然，我只是在讨论数字：

```js
console.log(typeof(28)); // "number"
console.log(typeof(3.14)); // "number"
console.log(typeof(-140)); // "number"
```

数字看起来平平无奇，我们仔细看看。

### 计算机中的数学

JavaScript 的数字和现实数学中的数字的行为并不太一样。这有段代码来说明：

```js
console.log(0.1 + 0.2 === 0.3); // false
console.log(0.1 + 0.2 === 0.30000000000000004); // true
```

这看起来非常的神奇！与一般的看法相反，这并不意味着 JavaScript 的程序出了什么问题。这个问题及时在其他编程语言中也很常见。它甚至有个名字：***浮点数***。

你看，JavaScript 并不代表着我们真实生活中的数学。浮点数计算是一个“计算机中的数学”。不要太在意这个名字或它的原理。很少的人能完全的解释清楚背后的事情。在实践中，即使你不去考虑它，也一样会工作的很好。不过，还是让我们快速看一下是什么造成了不同。

### 颜色和数字

你有没有用过扫描仪将物理照片或文档变成数字化的？这个比喻可以帮助我们理解 JavaScript 的数字。

扫描仪通常最多可以识别1600万种颜色。如果你用红色蜡笔画了一幅画，并扫描了它，产生的图片同样是红色 —— 但只是从这1600万种颜色中找了一个最接近的颜色。所以如果我们有两个差别非常小的红色蜡笔，扫描仪可能会很愚蠢地认为它们是一样的！

***我们可以说扫描仪判别颜色的精度有限。***

浮点数的运算很类似。在真实数学中，数字有无穷多个。但是在浮点数运算中，**只有18亿五千万个。** 所以在我们的代码中进行数学运算时，JavaScript 会找到它知道的最接近的数字 —— 就跟扫描仪对颜色一样。

我们可以想象所有的 JavaScript 的数字都在一个轴上。越接近 0 ，数字的精度越高，离旁边的数字也就越“近”。

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1580435620/just-javascript-email-images/jj04/number_axis.gif)

当我们从 0 开始往不同方向移动时，精度会逐渐减少。在某些点，JavaScript 中两个数的差距甚至超过了 1：

```js
console.log(Number.MAX_SAFE_INTEGER);     // 9007199254740991
console.log(Number.MAX_SAFE_INTEGER + 1); // 9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 2); // 9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 3); // 9007199254740994
console.log(Number.MAX_SAFE_INTEGER + 4); // 9007199254740996
console.log(Number.MAX_SAFE_INTEGER + 5); // 9007199254740996
```

幸运的是，在 `Number.MIN_SAFE_INTEGER` 和 `Number.MAX_SAFE_INTEGER` 之间的 **所有** 整数都是准确的。这也是为什么  `10 + 20 === 30`。

但是当我们写下 `0.1` 和 `0.2` 的时候，我们得到的并不是准确的 `0.1` 和 `0.2`。我们只是得到了在 JavaScript 中可用的最近的数字。它们几乎一样，但是还是有一些微小的差别。这些微小的差别相加，就造成了为什么 `0.1 + 0.2` 并没有得到准确的结果 `0.3`。

如果你仍然很困惑，别着急。你可以在[学习关于浮点计算的更多](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/vqh3hmu3rr6pqdcg/aHR0cHM6Ly9mbG9hdGluZy1wb2ludC1ndWkuZGUvZm9ybWF0cy9mcC8=) 中去了解，但是你已经比一开始了解的更多了。除非是在金融相关的软件中，大部分时间你都不用担忧它。

### 特殊数字

值得注意，在浮点数运算中包含了一些特殊数字。你可能偶尔会遇到 `NaN`, `Infinit`, `-Infinity` 和 `-0`。它们的之所以存在，是因为有时候你可能会执行一些类似 `1 / 0` 之类的操作，而要显示出结果。浮点运算标准规范了它们如何工作，以及当你使用它们时会发生什么。

这里展示了这些值如何进入到你的代码的:

```js
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

在这些特殊数字里，`NaN` 非常有趣，它是 `0 / 0` 或者其他一些非法数学运算的结果，表示着“不是一个数字”。

你可能会对这个声明说它是一个数字而感到困惑：

```js
console.log(typeof(NaN)); // "number"
```

然而，这并没什么问题。从 JavaScript 的观点来看，`NaN` 是一个数字类型的值。它不是 `null`, `undefined` 或者字符串。它是在浮点运算中，表示一个[”不是数字“](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/6qhehou6ee473rho/aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvTmFO)的东西。所以它是一个数字类型的值。之所以叫做”不是数字“，是因为它表示一个非法的结果。

在写代码的过程中，很少用到这些特殊数字。然而，它们可能会在代码出错的时候出现。所以最好还是了解它们的存在。

## 接下来

这一节分成了两部分。我们到达了第一部分的尾声，让我们稍微休息一下。回复一下我们目前为止数了几个值!

![image](https://user-images.githubusercontent.com/17036920/111267173-90429180-8666-11eb-89bc-4d4eec884f64.png)

- **未定义：** 只有一个值，`undefined`
- **空值：** 只有一个值，`null`
- **布尔：** 两个值，`true` 和 `false`。
- **数字：** 每个浮点数都有一个值

还学了一些 JavaScript 中关于数字的一些有趣的点：

- **在 JavaScript 中不能准确地表示所有数字。** 小数部分越接近 `0`， 精度就会越高，反之亦然。我们将小数点称为“浮点”。
- **类似 1/0 或者 0/0 的无效计算，会有特殊的值。** `NaN` 就是其中一个。它通常在代码出错的情况下出现。
- **`typeof(NaN)` 是一个数字，因为 `NaN` 是一个数字类型的值。** 它被称为“不是一个数字”，因为它代表了“无效”的数字。

第二部分，我们会继续这趟旅程。我们会去了解大整数、字符串、对象和函数 —— 试着数出每一个。


## 练习
[练习题](https://click.convertkit-mail.com/e5u45dk37xh0u0pe6gb7/8ghqh3upnn8oe9ck/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL0MzQWprND9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)
