layout: post
title: Prototypes
date: 2021-08-11
tags: JustJavascript
---

> from https://justjavascript.com/

在之前的章节里，我们讨论了对象、属性和可变性。看起来我们好像偏离了主题，但是我们就快要讨论完对象的各方面了！

这有一个测试你的思维模式的小脑筋急转弯：

```js
let pizza = {};
console.log(pizza.taste); // "pineapple"
```

问问你自己，这可能吗？

我们刚刚创建了一个空对象 `{}`。我确实没有在它被打印之前添加任何地属性。所以看起来 `pizza.taste` 是无法指向 `"pineapple"` 的。我们会期望 `pizza.taste` 会给我们 `undefined` 值。（在对象属性不存在的时候，返回 `undefined` 值，不是吗？）

然而，如果在这两行代码之前添加一些代码，会使得 `pizza.taste` 变成 `"pineapple"`！这可能是个刻意的例子，但它展示给了我们的 JavaScript 思维模式还不完整。

在这一章，我们将会介绍 ***原型*** 的概念。原型将会解释在这个谜题中发生了什么。更重要的是，原型是 JavaScript 的核心特性之一。有些人们忽视了对它的学习，因为它们太不寻常了。然而，核心的观念其实很简单。

## 原型

这里有两个变量指向了两个对象：

```js
let human = {
  teeth: 32
};

let gwen = {
  age: 19
};
```

我们可以用熟悉的方式来可视化展现它们：

![image](https://user-images.githubusercontent.com/17036920/115978259-a110ec00-a5b0-11eb-99a7-47c96948323d.png)

在这个例子中，`gwen` 指向了一个没有 `teeth` 属性的对象。按照我们学习的规则，如果我们读取这个对象，将会得到 `undefined`。

```js
console.log(gwen.teeth)
```

但是故事到这并没有结束。虽然默认情况下会返回 `undefined`，但是我们可以让 JavaScript ***从另外的对象中接着寻找当前对象不存在的属性。*** 我们可以用一行代码做到这个事：

```js
let human = {
  teeth: 32
};

let gwen = {
  // We added this line:
  __proto__: human,
  age: 19
};
```

这个神秘的 ``__proto__`` 属性是什么啊？

这表现了 JavaScript 原型的概念。任何 JavaScript 对象可以选择另外一个对象作为它的原型。我们很快将会在接下来的一些例子中讨论它们的意义。现在，让我们把 `__proto__` 想象成一根特殊的线。

![image](https://user-images.githubusercontent.com/17036920/115978372-5f347580-a5b1-11eb-8895-28f1f8007ae3.png)

花一点时间将这幅图和代码匹配一下。我们和之前一样画出这张图，唯一的不同是这条神秘的 `__proto__` 线。

通过这个特别的 `__proto__` （我们知道它是对象的原型），我们指示 JavaScript 接着在其他对象上去寻找不存在的属性。

### 原型的行为

在之前，我们如果尝试寻找 `gwen.teeth` 的话，我们会得到 `undefiend`。这是因为 `gwen` 变量指向的对象里面没有 `teeth` 这个属性。

但是感谢 `__proto__: human` 这一行，现在答案不一样了：

```js
let human = {
  teeth: 32
};

let gwen = {
  // "Look for other properties here"
  __proto__: human,
  age: 19
};

console.log(gwen.teeth); // 32
```

现在的流程大概是这样：

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1590534270/just-javascript-email-images/jj09/proto_anim.gif)

1. 顺着 `gwen` 的线，这是一个对象。
2. 这个对象有 `teeth` 这个属性吗？
  - 没有
  - **但它有个原型。** 让我们检查这个原型。
3. 这个对象有 `teeth` 这个属性吗？
  - 有的，它指向 `32`。
  - 因此， `gwen.teeth` 是 `32`。

这有点类似我们经常在工作会说：”我不知道，但是爱丽丝可能知道“。通过 `__proto__`，我们指示 JavaScript 去”问问别的对象“。

为了检查一下目前所学，写下你的答案：

```js
let human = {
  teeth: 32
};

let gwen = {
  __proto__: human,
  age: 19
};

console.log(human.age); // ?
console.log(gwen.age); // ?

console.log(human.teeth); // ?
console.log(gwen.teeth); // ?

console.log(human.tail); // ?
console.log(gwen.tail); // ?

```

### 停在这

在你没写完答案之前不要往下翻了

...

...

...

...

...

让我们检查一下你的答案。

`human` 变量指向一个对象，其中没有 `age` 属性，所以 `human.age` 是 `undefined`。`gwen` 变量指向一个对象，其中有 `age` 属性。这条线指向 `19`，所以 `gwen.age` 的值是 `19`：

```js
console.log(human.age); // undefined
console.log(gwen.age); // 19
```

`human` 变量指向的对象有 `teeth` 这个属性，所以 `human.teeth` 是 `32`。`gwen` 变量指向的对象没有 `teeth` 属性。但是，这个对象有一个原型，原型中有 `teeth` 属性。这也是为什么 `gwen.teeth` 也是 32.

```js
console.log(human.teeth); // 32
console.log(gwen.teeth); // 32
```

两个对象都没有 `tail` 属性，所以他们都是 `undefined`。

```js
console.log(human.tail); // undefined
console.log(gwen.tail); // undefined
```

注意，尽管 `gwen.teeth` 的值是 `32`，但这不表示 `gwen` 拥有了 `teeth` 属性！事实上，在这个例子里，`gwen` 是没有 `teeth` 属性的。但是它的原型对象 —— `human` 指向的那个对象 —— 是有这个属性的。

这个例子提醒我们 `gwen.teeth` 是一个表达式 —— 一个向 JavaScript 宇宙的提问 —— JavaScript 会根据一系列的步骤来回答它。现在我们知道在寻找一个属性的时候会有3个步骤。

### 原型链

原型不是 JavaScript 里一个特别的“事物”。原型更像一个 ***关系。*** 一个对象通过它的原型指向另外一个对象。

这自然会带来一个问题：如果我的对象的原型也有个它自己的原型呢？如果原型的原型也有原型呢？这怎么工作下午呢？

接下来的答案展示了它是如何工作的！

```js
let mammal = {
  brainy: true,
};

let human = {
  __proto__: mammal,
  teeth: 32
};

let gwen = {
  __proto__: human,
  age: 19
};

console.log(gwen.brainy); // true
```

我们看到 JavaScript 将会从我们的对象中寻找属性，然后从它的原型里，然后从原型的原型里，以此类推。我们只有在找完了所有的原型以后仍然没有找到这个属性的时候得到 `undefined`。

![image](https://user-images.githubusercontent.com/17036920/115979667-c524fb00-a5b9-11eb-9a9d-2af203a763c1.png)

这有点类似你在工作中说：“我不知道，但爱丽丝可能知道”。但是爱丽丝说：“我也不知道，去问问鲍勃。”最终，你讲找到答案，或者问完所有的人！

对象的这一系列去“寻找”的步骤就是我们所说的对象的原型链。（然而，和你可能穿戴的一些链不一样，原型链是不能循环的！）

### 遮蔽

考虑稍微改变一下例子：

```js
let human = {
  teeth: 32
};

let gwen = {
  __proto__: human,
  // This object has its own teeth property:
  teeth: 31
};
```

两个对象都定义了 `teeth` 属性，所以结果有些不同：

```js
console.log(human.teeth); // 32
console.log(gwen.teeth); // 31
```

注意 `gwen.teeth` 是 `31`。如果 `gwen` 没有它自己的 `teeth` 属性，我们会去原型链上寻找。但是因为 `gwen` 指向的对象有它自己的 `teeth` 属性，我们不需要接着去寻找就能得到答案。

![image](https://user-images.githubusercontent.com/17036920/115979888-20a3b880-a5bb-11eb-8a09-abdf47802676.png)

换句话说，一旦我们找到了属性， **就会停止搜寻。**

如果你想确定一个属性名是不是这个对象自己的属性，你可以使用内置的 `hasOwnProperty` 函数。它会对于“自己”的属性返回 `true`，并且不会关注原型。在我们最后的例子里，两个对象都有 `teeth` 这条线，所以它们都会返回 `true`：

```js
console.log(human.hasOwnProperty('teeth')); // true
console.log(gwen.hasOwnProperty('teeth')); // true
```

### 赋值

考虑这个例子：

```js
let human = {
  teeth: 32
};

let gwen = {
  __proto__: human,
  // Note: no own teeth property
};

gwen.teeth = 31;

console.log(human.teeth); // ?
console.log(gwen.teeth); // ?
```

在赋值之前，两个表达式的结果都是 32：

![image](https://user-images.githubusercontent.com/17036920/115980174-11be0580-a5bd-11eb-95b8-355809d61aa0.png)

然后我们执行这个赋值

```js
gwen.teeth = 31;
```

现在的问题是 `gwen.teeth` 应该响应哪条线呢？答案是，通常来说，赋值会发生在对象自己本身。

所以，`gwen.teeth = 31` 在 `gwen` 指向的对象里创建了一个新的自己的 `teeth` 属性。这对原型没有任何影响。

![image](https://user-images.githubusercontent.com/17036920/115980233-a163b400-a5bd-11eb-8aa7-90b7e3b16840.png)

结果是，`human.teeth` 仍然是32， 但是 `gwen.teeth` 现在成了31：

```js
console.log(human.teeth); // 32
console.log(gwen.teeth); // 31
```

我们可以用一个简单的经验法则来总结这些行为。

当我们读取对象中不存在的属性，我们会去原型链里寻找。如果原型链里都找不到，会得到 `undefined`。

但是当我们给对象里不存在的属性进行写入操作时，我们会在这个对象里创建一个属性。通常来说，原型不会参与这个过程。

### Object 原型

下面这个对象没有原型把？

```js
let obj = {};
```

试着在你的浏览器控制台运行以下代码：

```js
let obj = {};
console.log(obj.__proto__); // Play with it!
```

惊奇地发现，`obj.__proto__` 不是 `null` 或者 `undefined`！相反，你会看见一个有一堆属性的奇怪对象，包括 `hasOwnProperty`。

![image](https://user-images.githubusercontent.com/17036920/115980315-775ec180-a5be-11eb-9aeb-0b3b5b812a70.png)

首先，这看起来有点费解，先别在意。我们一直认为 `{}` 是创建了一个“空”对象。但在之后会发现，它不是空的！它有一个隐藏的 `__proto__` 线默认指向了 Object 原型。

这解释了为什么 JavaScript 对象看起来有一些“内置”属性：

```js
let human = {
  teeth: 32
};
console.log(human.hasOwnProperty); // (function)
console.log(human.toString); // // (function)
```

这些“内置”属性就是 Object 原型中存在的普通属性而已。我们的对象的原型是 Object 原型，所以我们可以访问它们。（这是在 JS 引擎内部实现的）。

### 一个没有原型的对象

我们刚学习了当用 `{}` 语法创建对象时会有一个特定的 `__proto__` 线指向默认的 Object 原型。但是我们同样知道我们可以改变 `__proto__`。你可能会想：我们可以把它设置成 `null` 吗?

```js
let weirdo = {
  __proto__: null
};
```

答案是肯定的 —— 这会导致对象彻底地没有原型。结果就是，它时区了所有对象的内置方法：

```js
console.log(weirdo.hasOwnProperty); // undefined
console.log(weirdo.toString); // undefined
```

你通常不会这样创建对象。然而，Object 原型本身也就是一个对象而已。它是一个没有原型的对象。

### 原型污染

现在我们知道 JavaScript 中的对象默认有同一个原型。让我们简要回顾一下关于可变性的那一章：

![image](https://user-images.githubusercontent.com/17036920/115980573-59925c00-a5c0-11eb-9e37-5678ca8e0476.png)

这幅图给了我们一个新的视野。如果 JavaScript 在原型上去寻找没有存在的属性，并且大量对象都共享了同样的原型，我们能通过改变原型，创建一个新的属性，让所有对象都能“显示”它吗？

让我们添加两行代码：

```js
let obj = {};
obj.__proto__.smell = 'banana';
```

我们改变了 Object 原型，添加了一个 `smell` 属性。结果是，两个侦探看起来都使用了香蕉味的气味：

```js
console.log(sherlock.smell); // "banana"
console.log(watson.smell); // "banana"
```

![image](https://user-images.githubusercontent.com/17036920/115980644-e3422980-a5c0-11eb-927d-524059c11706.png)

改变共享原型，我们通常称它为原型污染。

在过去，原型污染是一个流行地扩展 JavaScript 特性的方法。然而，这些年 web 社区认识到它是脆弱地，并且使得[添加新语言特性](https://click.convertkit-mail.com/lmuzv5oklnb6u3gn96tg/m2h7h6un3le234fm/aHR0cHM6Ly9lc2Rpc2N1c3Mub3JnL3RvcGljL2hhdmluZy1hLW5vbi1lbnVtZXJhYmxlLWFycmF5LXByb3RvdHlwZS1jb250YWlucy1tYXktbm90LWJlLXdlYi1jb21wYXRpYmxl)变得困难。尽量避免它。

现在你可以解释一开始的 Pineapple Pizza 之谜了！在开发工具里试一下吧！

## __proto__ 与 prototype

你可能会想知道：`prototype` 属性是什么？你可以在 [MDN](https://click.convertkit-mail.com/lmuzv5oklnb6u3gn96tg/z2hgh7udp8wxoxfp/aHR0cHM6Ly9kZXZlbG9wZXIubW96aWxsYS5vcmcvZW4tVVMvZG9jcy9XZWIvSmF2YVNjcmlwdC9SZWZlcmVuY2UvR2xvYmFsX09iamVjdHMvQXJyYXkvZmlsdGVy) 上去了解。

坏消息是：`prototype` 属性和原型的理念其实并没有什么关系。它更多的是关于 `new` 操作符的事情，我们还没有用到它。

记住， **`__proto` 的含义是一个对象的原型。** `prototype` 属性和 `new` 操作符是完全另外的话题，我们暂时会跳过它。

### 为什么这很重要？

在实践中，你可能不会在你的代码中直接使用原型。（事实上，直接使用 `__proto__` 语法本身都是[不提倡的。](https://click.convertkit-mail.com/lmuzv5oklnb6u3gn96tg/dphehmu7e25de2am/aHR0cHM6Ly8yYWxpdHkuY29tLzIwMTUvMDkvcHJvdG8tZXM2Lmh0bWw=)）

原型有一些反常规，许多人和框架并没有真正地如同范例般地拥抱它们。相反，人们经常用原型来构建其他编程语言中传统的“类继承”模型。事实上，这是如此普遍，以至于 JavaScript 中添加了类的语法，却把原型从视野中“隐藏”了起来。

尽管如此，你还是会注意到原型隐藏在类或者其他 JavaScript 特性“之下”。举个例子，这有段[代码](https://click.convertkit-mail.com/lmuzv5oklnb6u3gn96tg/e0hph0un7d4m7zc8/aHR0cHM6Ly9naXN0LmdpdGh1Yi5jb20vZ2FlYXJvbi9hMjVmZDQyYTFlNmI0Y2MyNDg1MTk3OGRmMGEzNjU3MQ==)，来展示 JavaScript 类通过重写 `__proto__` 来展示后台发生的事情。

个人来说，我不经常在我日常的代码中使用类，并且也很少直接使用原型。然而，这会帮助我们知道这些特性是如何建立起来的，以及当我们读或写一个对象的属性的时候，发生了什么。

## 回顾

- 当读取一个 `obj.prop` 时，如果 `obj` 没有 `prop` 属性， JavaScript 会接着从 `obj.__proto__.prop` 上去寻找，如果找不到，会接着从 `obj.__proto__.__proto__.prop` 去找，以此类推，知道找到这个属性或者是找完整个原型链。
- 当写入 `obj.prop` 时，JavaScript 通常直接在对象中写入，而不是在原型链中寻找。
- 我们可以使用 `obj.hasOwnProperty('prop')` 来查看对象是否有自己的 `prop` 属性。换句话说，它意味着是否有 `prop` 这个属性的线直接连接到对象。
- 我们可以通过修改原型对象来“污染”一个许多对象的共享原型。我们甚至可以在 Object 原型上这么做 —— 它是 `{}` 对象的默认原型！但是我们不应当这么做，除非只是搞个恶作剧。
- 你可能不会经常在实践中直接使用原型。然而，它是 JavaScript 对象如何工作的基础，可以帮助你更容易地了解它们背后的机制。一些高级的 JavaScript 特性，包括类，都是通过原型来构建的。

## 练习

[练习题](https://click.convertkit-mail.com/lmuzv5oklnb6u3gn96tg/7qh7h2u49xzd9gaz/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL1M3cDhOQj9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)

































































