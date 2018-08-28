
[Source](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0 "Permalink to Master the JavaScript Interview: What is Functional Programming?")

# Làm chủ cuộc phỏng vấn JavaScript: Lập trình hướng chức năng là gì?

![][1]

Cấu trúc Synth — Orihaus (CC BY 2.0)

> "Làm chủ cuộc phỏng vấn JavaScript" là một loạt các bài viết được thiết kế để chuẩn bị cho các ứng cử viên các câu hỏi phổ biến mà họ có khả năng gặp phải khi ứng tuyển vị trí JavaScript từ level mid đến senior-level. Đây là những câu hỏi tôi thường xuyên sử dụng trong các cuộc phỏng vấn thực tế.

Lập trình hướng chức năng đã trở thành một chủ đề thực sự nóng trong thế giới JavaScript. Chỉ vài năm trước, vài lập trình viên JavaScript đã biết lập trình hướng chức năng là gì, nhưng tất cả codebase của ứng dụng lớn mà tôi đã thấy trong 3 năm qua đều sử dụng nhiều ý tưởng lập trình hướng chức năng.

**Lập trình hướng chức năng** (thường được viết tắt là FP) là quá trình xây dựng phần mềm bằng cách tạo **hàm thuần túy**, tránh **trạng thái chia sẻ,** **dữ liệu có thể thay đổi,** và **tác dụng phụ**. Lập trình hướng chức năng là **declarative** thay vì **imperative**, và trạng thái ứng dụng truyền qua các hàm thuần túy. Tương phản với lập trình hướng đối tượng, nơi mà trạng thái ứng dụng thường được chia sẻ và được colocated với các phương thức trong đối tượng.

Lập trình hướng chức năng là **một mô hình lập trình**, có nghĩa rằng nó là một cách suy nghĩ về xây dựng phần mềm dựa trên một số nguyên tắc cơ bản, xác định (được liệt kê ở trên). Các ví dụ khác về mô hình lập trình bao gồm lập trình hướng đối tượng và lập trình hướng thủ tục.

Code hướng chức năng có xu hướng ngắn gọn hơn, dễ dự đoán hơn và dễ kiểm tra hơn code imperative hoặc đối tượng - nhưng nếu bạn không quen với nó và các mẫu phổ biến liên quan đến nó, code hướng chức năng cũng có thể dày đặc hơn và tài liệu liên quan có thể khó học đối với người mới.

Nếu bạn bắt đầu tra google thuật ngữ lập trình hướng chức năng, bạn sẽ nhanh chóng gặp phải các trở ngại của một bức tường của ngôn ngữ học thuật có thể rất đáng sợ cho người mới bắt đầu. Nói rằng nó có một đường cong học tập là nói dối. Nhưng nếu bạn đã lập trình JavaScript trong một thời gian, rất có thể là bạn đã sử dụng rất nhiều khái niệm và tiện ích lập trình hướng chức năng trong phần mềm thực têd của bạn.
> Đừng để tất cả những từ ngữ mới làm bạn sợ hãi. Nó dễ hơn rất nhiều .

Phần khó nhất là bạn luôn bị bao vây bởi các từ ngữ không quen thuộc. Có rất nhiều ý tưởng trong định nghĩa trong sáng ở trên mà tất cả mọi thứ cần phải được hiểu trước khi bạn có thể bắt đầu nắm bắt ý nghĩa của lập trình hướng chức nămh:

* Pure functions
* Function composition
* Avoid shared state
* Avoid mutating state
* Avoid side effects

Nói cách khác, nếu bạn muốn biết ý nghĩa  lập trình hướng chức năng trong thực tế, bạn phải bắt đầu với một sự hiểu biết về những khái niệm cốt lõi đó.

A **pure function** là một hàm mà:
* Với cùng các yếu tố đầu vào, luôn trả về cùng một đầu ra
* Không bị ảnh hướng bên ngoài

Các hàm thuần túy có rất nhiều thuộc tính quan trọng trong lập trình huowngcs chức năng, bao gồm **tính minh bạch tham chiếu** (bạn có thể thay thế một hàm gọi với giá trị kết quả của nó mà không thay đổi ý nghĩa của chương trình). Đọc ["Chức năng thuần túy là gì?"] [2] để biết thêm chi tiết.

**Function composition** là quá trình kết hợp hai hoặc nhiều chức năng để tạo ra một chức năng mới hoặc thực hiện một số tính toán. Ví dụ, thành phần `f. g` (dấu chấm có nghĩa là "hợp với") tương đương với `f (g (x))` trong JavaScript. Hiểu biết về function composition là một bước quan trọng hướng tới sự hiểu biết cách phần mềm được xây dựng bằng cách sử dụng lập trình hướng chức năng. Đọc ["Thành phần chức năng là gì?"] [3] để biết thêm.

### Shared State

**Shared State** là bất kỳ biến, đối tượng hoặc không gian bộ nhớ nào tồn tại trong một phạm vi chia sẻ hoặc là thuộc tính của một đối tượng được truyền giữa các phạm vi. Một phạm vi chia sẻ có thể bao gồm phạm vi toàn cục hoặc đóng kín. Thông thường, trong lập trình hướng đối tượng, các đối tượng được chia sẻ giữa các phạm vi bằng cách thêm các thuộc tính cho các đối tượng khác.

Ví dụ, một trò chơi máy tính có thể có một đối tượng trò chơi chính, với các nhân vật và các mục trò chơi được lưu trữ dưới dạng các thuộc tính thuộc sở hữu của đối tượng đó. Lập trình hướng chức năng tránh trạng thái chia sẻ - thay vào đó dựa vào cấu trúc dữ liệu không thay đổi và tính toán thuần túy để lấy dữ liệu mới từ dữ liệu hiện có. Để biết thêm chi tiết về cách phần mềm chức năng có thể xử lý trạng thái ứng dụng, hãy xem ["10 mẹo để có cấu trúc Redux tốt hơn"] [4].

Vấn đề với trạng thái chia sẻ là để hiểu tác động của một hàm, bạn phải biết toàn bộ lịch sử của mọi biến chia sẻ mà hàm sử dụng hoặc ảnh hưởng.

Hãy tưởng tượng bạn có một đối tượng người dùng cần lưu. Hàm `saveUser ()` của bạn tạo một yêu cầu tới một API trên máy chủ. Trong khi điều đó xảy ra, người dùng thay đổi hình ảnh hồ sơ của họ bằng `updateAvatar ()` và kích hoạt một yêu cầu `saveUser ()` khác. Khi lưu, máy chủ sẽ gửi lại một đối tượng người dùng chuẩn để thay thế bất kỳ thứ gì trong bộ nhớ để đồng bộ hóa với các thay đổi xảy ra trên máy chủ hoặc để đáp ứng các cuộc gọi API khác.

Thật không may, phản hồi thứ hai nhận được trước phản hồi đầu tiên, vì vậy khi phản hồi đầu tiên (hiện đã lỗi thời) được trả về, ảnh hồ sơ mới bị xóa trong bộ nhớ và được thay thế bằng ảnh cũ. Đây là một ví dụ về điều kiện chạy đua - một lỗi rất phổ biến liên quan đến trạng thái được chia sẻ.

Một vấn đề phổ biến khác liên quan đến trạng thái chia sẻ là việc thay đổi thứ tự mà các hàm được gọi có thể gây ra một loạt các lỗi vì các hàm hoạt động trên trạng thái chia sẻ phụ thuộc vào thời gian:

Ví dụ về sự phụ thuộc thời gian:

Khi bạn tránh trạng thái chia sẻ, thời gian và thứ tự của các lời gọi hàm không thay đổi kết quả của việc gọi hàm. Với các hàm thuần túy, được cung cấp cùng một đầu vào, bạn sẽ luôn nhận được cùng một đầu ra. Điều này làm cho các lời gọi hàm hoàn toàn độc lập với các lời gọi hàm khác, có thể đơn giản hóa triệt để các thay đổi và tái cấu trúc. Một thay đổi trong một hàm, hoặc thời gian của một lời gọi hàm sẽ không gấp khúc và phá vỡ các phần khác của chương trình.

Trong ví dụ trên, chúng ta sử dụng `Object.assign ()` và truyền vào một đối tượng rỗng làm tham số đầu tiên để sao chép các thuộc tính của `x` thay vì thay đổi nó tại chỗ. Trong trường hợp này, nó sẽ tương đương với việc tạo một đối tượng mới ngay từ đầu, không có `Object.assign ()`, nhưng đây là một mẫu phổ biến trong JavaScript để tạo ra các bản sao của trạng thái hiện tại thay vì sử dụng các biến đổi, ví dụ đầu tiên.

Nếu bạn xem xét kỹ các câu lệnh `console.log ()` trong ví dụ này, bạn sẽ thấy một cái gì đó mà tôi đã đề cập: function composition. Nhớ lại từ trước, thành phần hàm trông giống như sau: `f (g (x))`. Trong trường hợp này, chúng ta thay thế `f ()` và `g ()` bằng `x1 ()` và `x2 ()` cho thành phần: `x1. x2`.

Tất nhiên, nếu bạn thay đổi thứ tự của composition, đầu ra sẽ thay đổi. Thứ tự của các hoạt động vẫn còn quan trọng. `f (g (x))` không phải lúc nào cũng bằng `g (f (x))`, nhưng những gì không quan trọng nữa là những gì xảy ra với các biến bên ngoài hàm - và đó là một vấn đề lớn. Với hàm số không tinh khiết, bạn không thể hiểu đầy đủ chức năng của một hàm trừ khi bạn biết toàn bộ lịch sử của mọi biến mà hàm sử dụng hoặc ảnh hưởng.

Loại bỏ phụ thuộc thời gian lời gọi hàm và bạn sẽ loại bỏ toàn bộ lớp lỗi tiềm ẩn.

### Tính bất biến

Một đối tượng **immutable** là một đối tượng không thể sửa đổi sau khi nó được tạo ra. Ngược lại, một đối tượng **mutable** là bất kỳ đối tượng nào có thể được sửa đổi sau khi nó được tạo ra.

Tính bất biến là một khái niệm trung tâm về lập trình hướng chức năng bởi vì không có nó, luồng dữ liệu trong chương trình của bạn bị mất. Lịch sử trạng thái và các lỗi lạ có thể xâm nhập vào phần mềm của bạn. Để biết thêm về tầm quan trọng của bất biến, hãy xem ["Người Dao bất biến."] [5]

Trong JavaScript, điều quan trọng là không nhầm lẫn `const`, với bất biến. `const` tạo ra một ràng buộc tên biến mà không thể được gán lại sau khi tạo. `const` không tạo ra các đối tượng bất biến. Bạn không thể thay đổi đối tượng mà ràng buộc đề cập đến, nhưng bạn vẫn có thể thay đổi các thuộc tính của đối tượng, có nghĩa là các ràng buộc được tạo bằng `const` là có thể thay đổi, không thay đổi.

Các đối tượng bất biến không thể thay đổi được. Bạn có thể làm cho một giá trị thực sự bất biến bằng cách đóng băng sâu đối tượng. JavaScript có một phương thức đóng băng một đối tượng:

Nhưng các đối tượng bị đóng băng chỉ là bất biến bề ngoài. Ví dụ: đối tượng sau có thể thay đổi:

As you can see, the top level primitive properties of a frozen object can't change, but any property which is also an object (including arrays, etc…) can still be mutated — so even frozen objects are not immutable unless you walk the whole object tree and freeze every object property.

In many functional programming languages, there are special immutable data structures called **trie data structures** (pronounced "tree") which are effectively deep frozen — meaning that no property can change, regardless of the level of the property in the object hierarchy.

Tries use **structural sharing** to share reference memory locations for all the parts of the object which are unchanged after an object has been copied by an operator, which uses less memory, and enables significant performance improvements for some kinds of operations.

For example, you can use identity comparisons at the root of an object tree for comparisons. If the identity is the same, you don't have to walk the whole tree checking for differences.

There are several libraries in JavaScript which take advantage of tries, including [Immutable.js][6] and [Mori][7].

I have experimented with both, and tend to use Immutable.js in large projects that require significant amounts of immutable state. For more on that, see ["10 Tips for Better Redux Architecture"][4].

### Side Effects

A side effect is any application state change that is observable outside the called function other than its return value. Side effects include:

* Modifying any external variable or object property (e.g., a global variable, or a variable in the parent function scope chain)
* Logging to the console
* Writing to the screen
* Writing to a file
* Writing to the network
* Triggering any external process
* Calling any other functions with side-effects

Side effects are mostly avoided in functional programming, which makes the effects of a program much easier to understand, and much easier to test.

Haskell and other functional languages frequently isolate and encapsulate side effects from pure functions using [**monads**][8]. The topic of monads is deep enough to write a book on, so we'll save that for later.

What you do need to know right now is that side-effect actions need to be isolated from the rest of your software. If you keep your side effects separate from the rest of your program logic, your software will be much easier to extend, refactor, debug, test, and maintain.

This is the reason that most front-end frameworks encourage users to manage state and component rendering in separate, loosely coupled modules.

### Reusability Through Higher Order Functions

Functional programming tends to reuse a common set of functional utilities to process data. Object oriented programming tends to colocate methods and data in objects. Those colocated methods can only operate on the type of data they were designed to operate on, and often only the data contained in that specific object instance.

In functional programming, any type of data is fair game. The same `map()` utility can map over objects, strings, numbers, or any other data type because it takes a function as an argument which appropriately handles the given data type. FP pulls off its generic utility trickery using **higher order functions**.

JavaScript has **first class functions**, which allows us to treat functions as data — assign them to variables, pass them to other functions, return them from functions, etc…

A **higher order function** is any function which takes a function as an argument, returns a function, or both. Higher order functions are often used to:
* Abstract or isolate actions, effects, or async flow control using callback functions, promises, monads, etc…
* Create utilities which can act on a wide variety of data types
* Partially apply a function to its arguments or create a curried function for the purpose of reuse or function composition
* Take a list of functions and return some composition of those input functions

#### Containers, Functors, Lists, and Streams

A functor is something that can be mapped over. In other words, it's a container which has an interface which can be used to apply a function to the values inside it. When you see the word functor, you should think "mappable".

Earlier we learned that the same `map()` utility can act on a variety of data types. It does that by lifting the mapping operation to work with a functor API. The important flow control operations used by `map()` take advantage of that interface. In the case of `Array.prototype.map()`, the container is an array, but other data structures can be functors, too — as long as they supply the mapping API.

Let's look at how `Array.prototype.map()` allows you to abstract the data type from the mapping utility to make `map()` usable with any data type. We'll create a simple `double()` mapping that simply multiplies any passed in values by 2:

What if we want to operate on targets in a game to double the number of points they award? All we have to do is make a subtle change to the `double()` function that we pass into `map()`, and everything still works:

The concept of using abstractions like functors & higher order functions in order to use generic utility functions to manipulate any number of different data types is important in functional programming. You'll see a similar concept applied in [all sorts of different ways][9].

> "A list expressed over time is a stream."

All you need to understand for now is that arrays and functors are not the only way this concept of containers and values in containers applies. For example, an array is just a list of things. A list expressed over time is a stream — so you can apply the same kinds of utilities to process streams of incoming events — something that you'll see a lot when you start building real software with FP.

### Declarative vs Imperative

Functional programming is a declarative paradigm, meaning that the program logic is expressed without explicitly describing the flow control.

**Imperative** programs spend lines of code describing the specific steps used to achieve the desired results — the **flow control: How** to do things.

**Declarative** programs abstract the flow control process, and instead spend lines of code describing the **data flow: What** to do. The _how_ gets abstracted away.

For example, this **imperative** mapping takes an array of numbers and returns a new array with each number multiplied by 2:

Imperative data mapping

This **declarative** mapping does the same thing, but abstracts the flow control away using the functional `Array.prototype.map()` utility, which allows you to more clearly express the flow of data:

**Imperative** code frequently utilizes statements. A **statement** is a piece of code which performs some action. Examples of commonly used statements include `for`, `if`, `switch`, `throw`, etc…

**Declarative** code relies more on expressions. An **expression** is a piece of code which evaluates to some value. Expressions are usually some combination of function calls, values, and operators which are evaluated to produce the resulting value.

These are all examples of expressions:
    
    
    2 * 2  
    doubleMap([2, 3, 4])  
    Math.max(4, 3, 2)

Usually in code, you'll see expressions being assigned to an identifier, returned from functions, or passed into a function. Before being assigned, returned, or passed, the expression is first evaluated, and the resulting value is used.

### Conclusion

Functional programming favors:

* Pure functions instead of shared state & side effects
* Immutability over mutable data
* Function composition over imperative flow control
* Lots of generic, reusable utilities that use higher order functions to act on many data types instead of methods that only operate on their colocated data
* Declarative rather than imperative code (what to do, rather than how to do it)
* Expressions over statements
* Containers & higher order functions over ad-hoc polymorphism

### Homework

Learn & practice this core group of functional array extras:

Use map to transform the following array of values into an array of item names:

Use filter to select the items where points are greater than or equal to 3:

Use reduce to sum the points:

#### Explore the Series

### Level Up Your Skills

[Learn JavaScript with Eric Elliott][10]. If you're not a member, you're missing out!

![][11]

[1]: https://cdn-images-1.medium.com/max/1600/1*1OxglOpkZHLITbIKEVCy2g.jpeg
[2]: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976
[3]: https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0
[4]: https://medium.com/javascript-scene/10-tips-for-better-redux-architecture-69250425af44
[5]: https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd
[6]: https://github.com/facebook/immutable-js
[7]: https://github.com/swannodette/mori
[8]: https://en.wikipedia.org/wiki/Monad_%28functional_programming%29
[9]: https://github.com/fantasyland/fantasy-land
[10]: http://ericelliottjs.com/product/lifetime-access-pass/
[11]: https://cdn-images-1.medium.com/max/1600/1*3njisYUeHOdyLCGZ8czt_w.jpeg

  
