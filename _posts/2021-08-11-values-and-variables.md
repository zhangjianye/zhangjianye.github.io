layout: post
title: Values and variables
date: 2021-08-11
tags: Just Javascript
---

> from https://justjavascript.com/

我们将从一些代码片段开始。

```js
let reaction = 'yikes';
reaction[0] = 'l';
console.log(reaction);
```

你觉得会发生什么？如果你不清楚，也没关系，我们还没讲到这。**试着用你现有的 JavaScript 知识去回答**。

现在我希望你花一些时间写下你关于这段代码中每一行的思考。注意在你目前的思维模式中所有不确定的地方，然后也写下它们。如果有任何疑问，试着尽量地表述清楚。

### 稳住！
如果你没写完你的思考，别往下翻了

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

答案来啦！这段代码可能会打印出 `"yikes"` 或者抛出一个错误，这取决于你是否使用了[严格模式](https://click.convertkit-mail.com/qdu5qvk02rb8u838lzcg/9qhzhdu399o36ot9/aHR0cHM6Ly9kZXZlbG9wZXIubW96aWxsYS5vcmcvZW4tVVMvZG9jcy9XZWIvSmF2YVNjcmlwdC9SZWZlcmVuY2UvU3RyaWN0X21vZGU=)。**反正它永远不会打印出 `"likes"`。**

Yikes.

## 原始值是不可变的

你的答案对了吗？这看起来可能是个 JavaScript 面试中提出的无关紧要的小问题，但实际提出的也很少。尽管如此，它也启示了关于原始值的重要观点。

**我不能修改原始值**

我将会用一个小例子来解释它。字符串（是原始值）和数组（不是原始值，它们是对象！）有许多相似的地方。数组是一些元素的顺序集合，而字符串是一些字符的顺序集合。

```js
let arr = [212, 8, 506];
let str = 'hello';
```

你可以用同样的方式访问数组或者字符串的第一个元素或字符。这让字符串感觉起来和数组很像（但并不是！）：

```js
console.log(arr[0]); // 212
console.log(str[0]); // "h"
```

你可以改变数组的第一个元素：

```js
arr[0] = 420;
console.log(arr); // [420, 8, 506]
```

直观上感觉，字符串也可以做同样的操作：

```js
str[0] = 'j'; // ???
```

**但并不行。**

这是一个需要在我们的思维模式中加入的一个重点。字符串是一个原始值。这意味着很多事情！

**所有的原始值都是不可变的。** “不可变”代表着“只读”。你永远不能弄乱原始值。

如果你尝试给原始值设置一些属性，比如数字或字符串等等，JavaScript 不会让你这么做。它会静默地拒绝这个操作，或者抛出一个错误。这取决于你的代码运行在[哪个模式](https://click.convertkit-mail.com/qdu5qvk02rb8u838lzcg/9qhzhdu399o36ot9/aHR0cHM6Ly9kZXZlbG9wZXIubW96aWxsYS5vcmcvZW4tVVMvZG9jcy9XZWIvSmF2YVNjcmlwdC9SZWZlcmVuY2UvU3RyaWN0X21vZGU=)。

但是请放心，下面的代码永远行不通：

```js
let fifty = 50;
fifty.shades = 'gray'; // No!
```

和所有数字一样，`50` 是一个原始值，你不能给她设置任何属性。

[你做不到](https://click.convertkit-mail.com/qdu5qvk02rb8u838lzcg/7qh7h2upzzrppoiz/aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g_dj1vdENwQ24wbDRXbw==)

在我的 JavaScript 宇宙，所有的原始值都位于离我的代码较远的空间中 —— 像遥远的星星。这提醒我即使我能从我的代码里引用它们，但是我却不能修改它们。它们就只能在那。

***这令人惊讶***

![image](https://user-images.githubusercontent.com/17036920/110886345-741bb900-8323-11eb-9157-733a204f7b11.png)

## 矛盾？

我刚刚展示了原始值是只读的 —— 或者，按我们的说法来说，它是不可变的。这有段代码来测试你的思维模式。

```js
let pet = 'Narwhal';
pet = 'The Kraken';
console.log(pet); // ?
```

跟之前一样。写下一些你的思考。不要太快。认真的思考每一行代码，一步一步来。字符串的不可变性在这里扮演了什么角色？

### 莫慌！

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

如果你意识到我在试图搞乱你的脑子，你是对的！答案是 `"The Kraken"` —— 不可变性在这没有起到任何作用。

如果你错了，也别丧气，我们还没讲到那！最后这两个例子看起来似乎有些互相矛盾。

***这是一个重要的认识***

如果你刚开始使用一个语言，可能会倾向于忽略这个矛盾。毕竟，如果你关注每个矛盾的话，你会陷入到一个很深的兔子洞中，学不到任何东西。但是现在你是在准备构建一个思维模式，你需要对矛盾有所怀疑。它们揭示了思维模式的差距。

## 变量是导线

我们再看一次这个例子。

```js
let pet = 'Narwhal';
pet = 'The Kraken';
console.log(pet); // "The Kraken"
```

我们直到字符串值是原始值，它不能被修改。但是 `pet` 变量去变成了 `"The Kraken"`。发生了什么呢？

这看起来似乎有点矛盾，但其实并没有。我们只是说***原始值不能修改***。我们没有说***变量***不能修改！

在重构我们的思维模式的时候，我们需要理清一些概念。

**变量不是值**

**变量指向值**

在我的宇宙里，变量就是导线。它有两个端点和一个方向：从我的代码中给它起的名字开始，链接到我的宇宙中的一些值。

举个例子，我看可以将 `pet` 变量指向 `"Narwhal"` 值。

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1579283157/just-javascript-email-images/jj03/narwhal-assignment.gif)

对于变量，我可以做两件事。

### 给变量赋值

其中一个是我们可以把一些值***赋予***变量：

```js
pet = 'The Kraken';
```

![](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1579283157/just-javascript-email-images/jj03/kraken-reassignment.gif)

在这里做的所有事就是给 JavaScript 一个指令，让它将“导线”的左边（我的 `pet` 变量）指向右边(`"The Kraken"`)。它将会在我下次重新赋值之前保留这个值。

注意我们不能再左边放任何东西

```js
'war' = 'peace'; // Nope. (Try it in the console.)
```

**一个赋值的左边必须是一个“导线”**。目前为止，我们仅仅知道变量是“导线”。但是之后我们会讨论另外一种“导线”。或许，你可以猜一下？（提示：它包括中括号或者点，我们已经见到它很多次了。）

还有另外一条规则。

**赋值的右边必须是个表达式。**它可以很简单，比如 `2` 或者 `'hello'`，或者也可能是相对复杂的表达式 —— 举个例子：

```js
pet = count + ' Dalmatians';
```

在这里，`count + 'Dalmatians'` 是一个表达式 —— 一个给 JavaScript 的问题。JavaScript 会用值来回答它（举个例子，`"101Dalmatians"`）。然后，`pet` “导线”会链接到这个值。

如果右边必须是一个表达式，意味着代码中的数字 `2` 或者字符串 `The Kranken` 也是表达式吗？是的！有些表达式叫做***字面量*** —— 因为它在字面上就写下了值。

## 从变量中读取值

我也可以从变量中***读取***值 —— 举个例子，为了打印一个值：

```js
console.log(pet);
```

这不足为奇。

但是注意，我们不是把 `pet` 变量传进了 `console.log`。这样说可能有些口语化，但是我们不能真正地将一个***变量***传进一个***函数***。我们传入的是 `pet` 变量目前的值。它是怎么工作的呢？

事实证明，像 `pet` 这样的变量名也可以如同表达式一样！当我们写下 `pet`，我们在问 JavaScript: “`pet` 现在的值是什么？”为了回答这个问题，JavaScript 顺着 `pet` 的导线，在另一端找到了一个值给我们。

所以同一个表达式可以在不同时候得到不同的值！

## 名词和动词
谁会关心“传入一个变量”或者“传入一个值”这样的说法吗？它们有很大的差异吗？我确信你不应该为了纠正它们而打扰你的同事 —— 甚至你自己。它会浪费每个人的时间。

但是在你的脑海中应当清楚对于每个概念***你能做什么***。你不能用单车来溜冰。你不能再真空中飞行。你不能和一只蚊子唱歌。所以你不能传入一个变量 —— 至少在 JavaScript 中是这样。

这有个例子说明为什么他们很重要。

```js
function double(x) {
  x = x * 2;
}

let money = 10;
double(money);
console.log(money); // ?
```

如果我们认为 `double(money)` 传入了一个***变量***，我们会期望 `x = x * 2` 会让这个变量乘以2.但是并不是这样的。我们知道 `double(money)` 意味着“找出 `money` 变量的***值***，然后将这个***值***传给 `double`”。所以答案是10。真是够诡异的！

在你的脑海中，JavaScript 的动词和名词有什么差异？我们如何联系他们？写下你常用的一些清单出来。

##放在一起

现在让我们回头看看***思维模式***那一章的例子。

```js
let x = 10;
let y = x;
x = 0;
```

我猜想你坑你在纸或者某个 [app](https://click.convertkit-mail.com/qdu5qvk02rb8u838lzcg/n2hohqu5rrz5k5i6/aHR0cHM6Ly93d3cuZXhjYWxpZHJhdy5jb20v) 上画出了 `x` 和 `y` 变量每一步之间的“导线”。

**第一条线没做什么事**

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1579283157/just-javascript-email-images/jj03/assign-step1.gif)

- 声明一个名为 x 的变量
  -  以 x 为起点画出一条导线
- 将 10 赋值给 x
  - **将 x 的导线指向 10 这个值** 

**第二条线很短，但是它做了一些事**

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1579283157/just-javascript-email-images/jj03/assign-step2.gif)

- 声明了一个名为 y 的变量
  - 给 y 变量一个导线
- 将 x 的值赋给 y
  - 计算表达式 x
    - 我们想问的“问题”是 x
    - **顺着 x 的导线 —— 答案是 10 这个值
  - x 表达式的结果是 10 这个值
  - 因此赋给 y 的值是 10
  - **将 y 的导线指向 10 这个值

**最后，我们得到第三条线**

![img](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1579283157/just-javascript-email-images/jj03/assign-step3.gif)

- 将 0 这个值赋给 x
  - **将 x 的导线指向 0 这个值** 

最后，`x` 变量指向了 `0` 这个值，`y` 变量指向了 `10` 这个值。注意 `y = x` 并不意味着将 `y` 指向 `x`。我们不能让变量互相连接。`变量总是指向一个值`。当我们看见赋值，我们“问”出右边的值，然后将左边的“导线”指向它。

我提到过一些 ***思维模式*** 通常将变量想成盒子。在这个宇宙中，我们不再用盒子这种说法了。**只有导线！**这可能看起来有点恼人。为什么我们不能将 10 这个值放入变量，而是要将变量指向它们？

使用导线这个概念非常重要，这是为了解释一些其他概念，比如严格相等，对象识别以及可变性等等。我们坚持使用导线这个说法，所以你不妨现在就开始习惯它们！

***我的宇宙充满了导线***

## 回顾

- **原始值不可变。** 在我们的代码中没有任何方法可以影响或改变它们。它们就在那。举个例子，我们不能给字符串值设置一个属性，因为它是原始值。数组不是原始值，所以我们可以给它设置属性。
- **变量不是值。** 每个变量指向了一个特定的值。我们可以使用 `=` 赋值操作符来改变变量指向哪个值。
- **变量像一个导线。** “导线”不是 JavaScript 的概念 —— 但是可以帮助我们想象变量如何指向值。除开变量还有些其他的“导线”，我们还没谈论到它们。
- **找出矛盾。** 如果学习过程中有两个事情看起来是矛盾的，别丧气。很可能这标志着一些更深的真相藏了起来。
- **动词和名词。** 我们正在构建一个思维模式，以便于我们可以更清楚地知道我们的宇宙中哪些是可行的，哪些是不行的。偶尔说说草率一些无妨，但是思考的时候就必须准确了。

## 练习
[练习题](https://click.convertkit-mail.com/qdu5qvk02rb8u838lzcg/owhkhwuloo2l7dav/aHR0cHM6Ly9lZ2doZWFkaW8udHlwZWZvcm0uY29tL3RvL1JXSmczbT9lbWFpbD15eXV1cXFpaUBvdXRsb29rLmNvbQ==)






















