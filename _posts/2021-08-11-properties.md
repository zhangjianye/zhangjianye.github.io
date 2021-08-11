layout: post
title: Properties
date: 2021-08-11
tags: Just Javascript
---

> from https://justjavascript.com/


让我们认识一下夏洛克-福尔摩斯，一个来自伦敦的世界著名侦探：

```js
let sherlock = {
  surname: 'Holmes',
  address: { city: 'London' } 
};
```

他的朋友约翰-华生最近和夏洛克一起居住了：

```js
let john = {
  surname: 'Watson',
  address: sherlock.address
};
```

夏洛克是一个聪明的侦探，但却是一个糟糕的室友。有一天，约翰受够了他。约翰改变了他的名字并且搬到了马里布：

```js
john.surname = 'Lennon';
john.address.city = 'Malibu';
```

练习时间！**对以下问题写下你的答案:**

```js
console.log(sherlock.surname); // ?
console.log(sherlock.address.city); // ?
console.log(john.surname); // ?
console.log(john.address.city); // ?
```

在你之后回来读这段代码之前，我希望你能有些新的感觉。打开你的纸笔或者任何可以涂鸦的 app，**画出你的思维模式和每条发生的线索。** 如果你不知道该如何表达，没关系。我们还没有讨论这个话题，尽可能地去猜一下吧。

然后，根据你最后的草稿，回答上面4个问题。

### 在这停住！
在你回答之前，别往下滚动了！

...

...

...

...

...

...

让我们看看答案：

```js
console.log(sherlock.surname); // "Holmes"
console.log(sherlock.address.city); // "Malibu"
console.log(john.surname); // "Lennon"
console.log(john.address.city); // "Malibu"
```

我没有写错 —— 它们确实 **都是 Malibu** 。这对夏洛克来说可真不友好！对于错误的思维模式，可能会认为 `sherlock.address.city` 应该是 "London" —— 但不是的。

为了了解原因，我们需要学习在 JavaScript 宇宙中属性是如何工作的。

## 属性

我们在之前讨论过对象。举个例子，这有一个 `sherlock` 变量指向了一个对象值。我们通过 `{}` 创建了一个新的对象：

```js
let sherlock = {};
```

在我们的宇宙中，它看起来是这样：

![image](https://user-images.githubusercontent.com/17036920/115647693-db7f4c80-a356-11eb-8266-24957c89bafd.png)

然而，对象通常会用于将一组有关的数据放在一起。举个例子，我们可能会有对于夏洛克所了解的一组不同的东西：

```js
let sherlock = {
  surname: 'Holmes',
  age: 64,
};
```

在这， `sherlock` 还是一个变量，但是 `surname` 和 `age` 却不同。它们是**属性。** 和变量不一样，属性属于一个特定的对象。

**在我们的 JavaScript 宇宙里，属性和变量都有“线”。** 然而，属性的线是从我们代码里的对象开始的。

在这，我们可以看到 `sherlock` 变量指向了我们创建的对象。这个对象有两个**属性。** 它的 `surname` 属性指向了 `Holmes` 这个字符串值，它的 `age` 属性指向了 `64` 这个数字值。

重要的是，属性**不包含值** —— 它们指向它们！这表明在我们的宇宙中充满了线。有一些线是从我们的代码（变量）开始的，有一些是从对象（属性）开始的。这些线都指向了值。

在读到这段之前，你可能会想象这些值是在对象“里面”的，因为在代码中看起来是这样。这个直接通常会带来一些错误，所以我们要“通过线来思考”来代替。再看看代码和对应的图。在你继续之前确认你已经充分了解并接受了这个观点。

### 读取一个属性

我们可以通过“点符号”来读取一个属性当前的值：

```js
console.log(sherlock.age); //64
```

在这，`sherlock.age` 是我们的老朋友 —— 一个表达式，一个对 JavaScript 宇宙的问题。为了回答它，JavaScript 从一开始顺着 `sherlock` 的线去寻找：

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1584416479/just-javascript-email-images/jj07/sherlock_readage.gif)

这条线把它带到了一个对象。从这个对象，JavaScript 顺着 `age` 属性接着寻找。

我们的对象中的 `age` 属性指向了 `64`， 所以 `sherlock.age` 的结果是 `64`。

### 属性名

属性都有名字。一个对象不能有两个同样名字的属性。举个例子，我们的对象不能有两个叫 `age` 的属性。

属性名是大小写敏感的！举个例子， `age` 和 `Age` 在 JavaScript 中是完全不同的两个属性。

如果我们之前不知道属性名是什么，但是我们有在代码中有一个字符串的值，我们可以使用 `[]` “中括号符” 从对象中读取它们：

```js
let sherlock = { surname: 'Holmes', age: 64 };
let propertyName = prompt('What do you want to know?');
alert(sherlock[propertyName]); // Read property by its name
```

在浏览器控制台试试这段代码，并在弹框中输入 "age" 。

### 给属性赋值

当我们给一个属性赋值的时候，发生了什么？

```js
sherlock.age = 65; 
```

让我们通过 `=` 把这段代码分成左边和右边。

**首先，我们通过左边找到了 `serlock.age` 这条线:**

顺着 `shecrlock` 这条线，我们找到了 `age` 属性这条线：

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1584416479/just-javascript-email-images/jj07/sherlock_reassign_age-1.gif)

注意我们没有顺着这条线找到 `64`。我们不关心现在的值是什么。在赋值的左边，我们只关心这条**线本身。**

还记得我们找到了哪条线？接着来吧。

**接下来，我们找到右边的值：65.**

和左边不同，赋值右边通常都表示一个值。在这个例子中，右边的值是数字值 `65`。让我们找到它:

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1584416480/just-javascript-email-images/jj07/sherlock_reassign_age-2.gif)

现在可以运行这个赋值了。

**最后，我们将左边的线连上右边的值：**

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1584416479/just-javascript-email-images/jj07/sherlock_reassign_age-3.gif)

### 缺失的属性

你可能会对如果我们读取一个不存在的属性时发生什么感到好奇：

```js
let sherlock = { surname: 'Holmes', age: 64 };
console.log(sherlock.boat); // ?
```

我们知道 `sherlock.boat` 是一个属性表达式。JavaScript 宇宙会用一些规则来决定用什么值来“回答”我们。

**规则如下：**

1. 找出点（.）左边的值。
2. 如果这个值是 `null` 或者 `undefined` 的话，立即抛出错误。
3. 如果不是，检查这个属性名在我们的对象中存在。
  - 如果存在，就用这个属性指向的值来回答。
  - 如果不存在，用 `undefined` 来回答。

注意这些规则有些过于简单，在未来我们还会修正它。目前为止，它们还是会告诉我们许多关于 JavaScript 如何工作的！

举个例子，`sherlock` 指向了一个**没有** `boat` 属性的对象。所以 `sherlock.boat` 会用一个 `undefined` 作为答案给我们：

```js
let sherlock = { surname: 'Holmes', age: 64 };
console.log(sherlock.boat); // undefined
```

注意**这不意味着**我们的对象有一个 `boat` 属性指向了 `undefined`！它只有两个属性，都不叫作 `boat`：

![image](https://user-images.githubusercontent.com/17036920/115651390-a62a2d00-a35d-11eb-8368-711cbcdef95f.png)

很容易将 `sherlock.boat` 直接对应到我们思维模式中属性的概念，但是**这不太对。** 这是 JavaScript 引擎的问题 —— 引擎遵循这些规则来回答。

这看起来像是 `sherlock` 对象指向了看起来并不存在的 `boat` 属性，并且返回了一个 `undefined` 值给我们，这不过是因为**规则是这样。** 没有更深的理由：计算机遵循规则。

往上滚动到之前的规则，再读一遍。你能做下面这个练习吗？

```js
let sherlock = { surname: 'Holmes', age: 64 };
console.log(sherlock.boat.name); // ?
```

运行这段代码会发生什么？**不要猜 —— 遵循规则。**

提示：这有两个点，所以你需要遵循两次规则

### 停在这！

在有答案之前不要继续向下

...

...

...

...

...

答案是 `sherlock.boat.name` 这个表达式会抛出错误：

- 我们首先需要找到 `sherlock.boat` 的值
  - 为了这个目的，我们先要找到 `sherlock` 的值。
    - `sherlock` 变量的值指向了一个对象
    - 因此 `sherlock` 的值是一个对象
  - 对象不是 `null` 或者 `undefined`， 所以我们继续。
  - 这个对象没有 `boat` 这个属性。
  - 因此 `sherlock.boat` 的值是 `undefined`。
- 我们在点（.）左边得到了 `undefined` 值。
- 规则说如果 `undefined` 或者 `null` 在左边的话需要抛出一个错误。

```js
let sherlock = { surname: 'Holmes', age: 64 };
console.log(sherlock.boat); // undefined
console.log(sherlock.boat.name); // TypeError!
```

如果还是很困惑的话，回到之前，一条一条按着规则来。

## 回顾

- 属性也是线 —— 有些像变量。它们也指向值。和变量不同，属性在我们的宇宙中是**从对象开始**的。
- 属性有名字。属性属于特定的对象。你不能再一个对象中拥有多个同名的属性。
- 通常，你可以通过三个步骤来执行赋值操作：
  - 找出左边的线
  - 找出右边的值
  - 将线指向值
- 一个表达式诸如 `obj.property` 通过以下步骤来计算：
  1.  找出点左边的值
  2.  如果是 `null` 或者 `undefined` 的话，就抛出错误。
  3.  如果属性存在，返回属性指向的值。
  4.  如果不存在的话，返回 `undefined` 这个值。

注意这个属性的思维模式还是过于简单。它对于接下里的一些章节还是足够了，但在未来我们会扩展它。

如果你在开始对夏洛克-福尔摩斯的例子感到困惑，你可以选择性地回去通过我们的新思维模式再重新试一遍。接下来的章节将会包含一些细节，如果你仍然不太确定为什么会这样，试着将属性也看成线。

## 练习
[练习题](https://click.convertkit-mail.com/8ku639o8wef3ulllwwal/6qhehouddeqe27ho/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL0lESkJQUT9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)



























