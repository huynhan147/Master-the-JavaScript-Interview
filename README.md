
[Source](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0 "Permalink to Master the JavaScript Interview: What is Functional Programming?")

# Làm chủ cuộc phỏng vấn JavaScript: Lập trình hướng chức năng là gì?

![][1]

Cấu trúc Synth — Orihaus (CC BY 2.0)

> "Làm chủ cuộc phỏng vấn JavaScript" là một loạt các bài viết được thiết kế để chuẩn bị cho các ứng cử viên các câu hỏi phổ biến mà họ có khả năng gặp phải khi ứng tuyển vị trí JavaScript từ mid đến senior-level. Đây là những câu hỏi tôi thường xuyên sử dụng trong các cuộc phỏng vấn thực tế.

Lập trình hướng chức năng đã trở thành một chủ đề thực sự nóng trong thế giới JavaScript. Chỉ vài năm trước,chỉ vài lập trình viên JavaScript biết lập trình hướng chức năng là gì, nhưng tất cả codebase của những ứng dụng lớn mà tôi đã thấy trong 3 năm qua đều sử dụng nhiều ý tưởng từ lập trình hướng chức năng.

**Lập trình hướng chức năng** (thường được viết tắt là FP) là quá trình xây dựng phần mềm bằng cách tạo **hàm thuần túy**, tránh **trạng thái chia sẻ,** **dữ liệu có thể thay đổi,** và **tác dụng phụ**. Lập trình hướng chức năng là **declarative** thay vì **imperative**, và trạng thái ứng dụng truyền qua các hàm thuần túy. Tương phản với lập trình hướng đối tượng, nơi mà trạng thái ứng dụng thường được chia sẻ và được colocated với các phương thức trong đối tượng.

Lập trình hướng chức năng là **một mô hình lập trình**, có nghĩa rằng nó là một cách suy nghĩ về xây dựng phần mềm dựa trên một số nguyên tắc cơ bản, xác định (được liệt kê ở trên). Các ví dụ khác về mô hình lập trình bao gồm lập trình hướng đối tượng và lập trình hướng thủ tục.

Code hướng chức năng có xu hướng ngắn gọn hơn, dễ dự đoán hơn và dễ kiểm tra hơn code imperative hoặc đối tượng - nhưng nếu bạn không quen với nó và các pattern phổ biến liên quan đến nó, code hướng chức năng cũng có thể dày đặc hơn và tài liệu liên quan có thể khó học đối với người mới.

Nếu bạn bắt đầu tra google thuật ngữ lập trình hướng chức năng, bạn sẽ nhanh chóng gặp phải các trở ngại của một bức tường của ngôn ngữ học thuật có thể rất đáng sợ cho người mới bắt đầu. Nói rằng nó có một đường cong học tập là nói dối. Nhưng nếu bạn đã lập trình JavaScript trong một thời gian, rất có thể là bạn đã sử dụng rất nhiều khái niệm và tiện ích lập trình hướng chức năng trong phần mềm thực tế của bạn.
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

Các hàm thuần túy có rất nhiều thuộc tính quan trọng trong lập trình hướng chức năng, bao gồm **tính minh bạch tham chiếu** (bạn có thể thay thế một hàm gọi với giá trị kết quả của nó mà không thay đổi ý nghĩa của chương trình). Đọc ["Chức năng thuần túy là gì?"] [2] để biết thêm chi tiết.

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

Như bạn có thể thấy, các thuộc tính nguyên thủy cấp cao nhất của một đối tượng bị đóng băng không thể thay đổi, nhưng bất kỳ thuộc tính nào cũng là một đối tượng (bao gồm mảng, vv…) vẫn có thể bị thay đổi - vì vậy ngay cả đối tượng bị đóng băng cũng không thay đổi trừ khi bạn duyệt toàn bộ cây đối tượng và đóng băng mọi thuộc tính đối tượng.

Trong nhiều ngôn ngữ lập trình chức năng, có cấu trúc dữ liệu bất biến đặc biệt gọi là **cấu trúc dữ liệu trie** (phát âm là "cây") được đóng băng sâu - nghĩa là không có thuộc tính nào có thể thay đổi, bất kể mức độ của thuộc tính trong hệ thống phân cấp đối tượng .

Các trie sử dụng **chia sẻ cấu trúc** để chia sẻ các vị trí bộ nhớ tham chiếu cho tất cả các phần của đối tượng không thay đổi sau khi đối tượng đã sao chép một toán tử, sử dụng ít bộ nhớ hơn và cho phép cải thiện hiệu suất đáng kể đối với một số loại hoạt động.

Ví dụ, bạn có thể sử dụng so sánh nhận dạng tại gốc của cây đối tượng để so sánh. Nếu danh tính giống nhau, bạn không phải duyệt cả cây để kiểm tra sự khác biệt.

Có một số thư viện trong JavaScript tận dụng các trie, bao gồm [Immutable.js] [6] và [Mori] [7].

Tôi đã thử nghiệm với cả hai, và có xu hướng sử dụng Immutable.js trong các dự án lớn đòi hỏi một lượng đáng kể trạng thái bất biến. Để biết thêm về điều đó, hãy xem ["10 mẹo để có cấu trúc Redux tốt hơn"] [4]

### Ảnh hưởng phụ

Một ảnh hưởng phụ là bất kỳ thay đổi trạng thái của ứng dụng nào mà có thể quan sát được bên ngoài hàm được gọi, ngoài giá trị trả về của nó. Các ảnh hưởng phụ bao gồm:

* Sửa đổi bất kỳ biến bên ngoài hoặc thuộc tính đối tượng nào (ví dụ: biến toàn cầu hoặc biến trong chuỗi phạm vi hàm chính)
* Đăng nhập vào bảng điều khiển
* Viết lên màn hình
* Viết vào một file
* Viết vào một mạng
* Kích hoạt bất kỳ tiến trình bên ngoài nào
* Gọi bất kỳ hàm nào với ảnh hưởng phụ

Ảnh hưởng phụ nên phải tránh trong lập trình hướng chức năng, làm cho hiệu quả của một chương trình dễ hiểu hơn nhiều và dễ dàng hơn nhiều để kiểm tra.

Haskell và các ngôn ngữ chức năng khác thường tách biệt và đóng gói các ảnh hưởng phụ từ các hàm thuần túy bằng [**monads**] [8]. Chủ đề của các monads là đủ sâu để viết thành một cuốn sách, vì vậy chúng tôi sẽ lưu lại nó cho sau này.

Những gì bạn cần biết ngay bây giờ là các ảnh hưởng phụ cần phải được tách biệt với phần còn lại của phần mềm của bạn. Nếu bạn giữ các hiệu ứng phụ tách biệt với phần còn lại của logic chương trình, phần mềm của bạn sẽ dễ dàng hơn để mở rộng, tái cấu trúc, gỡ lỗi, kiểm tra và bảo trì.

Đây là lý do mà hầu hết các framework front-end khuyến khích người dùng quản lý hiển thị trạng thái và thành phần trong các mô-đun riêng lẻ, tách biệt nhau.

### Khả năng tái sử dụng thông qua các chức năng bậc cao

Lập trình hướng chức năng có xu hướng tái sử dụng lại một tập hợp các tiện ích chức năng phổ biến để xử lý dữ liệu. Lập trình hướng đối tượng có xu hướng sắp xếp phương thức và dữ liệu trong các đối tượng. Những phương được pháp sắp xếp chỉ có thể hoạt động trên loại dữ liệu mà chúng được thiết kế để hoạt động và thường chỉ có dữ liệu chứa trong cá thể đối tượng cụ thể đó.

Trong lập trình hướng chức năng, bất kỳ loại dữ liệu nào là trò chơi công bằng. Cùng một tiện ích `map ()` có thể ánh xạ đối tượng, chuỗi, số hoặc bất kỳ kiểu dữ liệu nào khác vì nó lấy hàm làm đối số xử lý thích hợp kiểu dữ liệu đã cho. FP rút ra thủ thuật tiện ích chung của nó bằng cách sử dụng **các hàm bậc cao hơn**.

JavaScript có **các hàm lớp đầu tiên**, cho phép chúng ta xử lý các hàm như dữ liệu - gán chúng cho các biến, chuyển chúng đến các hàm khác, trả về chúng từ các hàm, v.v.

Hàm **bậc cao hơn** là bất kỳ hàm nào nhận hàm làm đối số, trả về hàm hoặc cả hai. Các hàm bậc cao thường được sử dụng để:

* Tóm tắt hoặc cô lập hành động, hiệu ứng hoặc điều khiển luồng không đồng bộ bằng cách sử dụng hàm callback, promise, monad, v.v.
* Tạo các tiện ích có thể hoạt động trên nhiều loại dữ liệu khác nhau
* Áp dụng một phần hàm cho các đối số của nó hoặc tạo một hàm được kết hợp với mục đích sử dụng lại hoặc hàm hợp
* Lấy danh sách các hàm và trả về một số thành phần của các hàm đầu vào đó

#### Containers, Functors, Lists, and Streams

Một functor là cái gì đó có thể được ánh xạ qua. Nói cách khác, nó là một container có một giao diện có thể được sử dụng để áp dụng một hàm cho các giá trị bên trong nó. Khi bạn nhìn thấy từ functor, bạn nên nghĩ rằng "có thể ánh xạ".

Trước đó chúng ta đã biết rằng cùng một tiện ích `map ()` có thể hoạt động trên nhiều kiểu dữ liệu khác nhau. Nó làm điều đó bằng cách nâng hoạt động ánh xạ để làm việc với một API functor. Các hoạt động kiểm soát lưu lượng quan trọng được sử dụng bởi `map ()` tận dụng giao diện đó. Trong trường hợp của `Array.prototype.map ()`, vùng chứa là một mảng, nhưng các cấu trúc dữ liệu khác cũng có thể là các hàm functors - miễn là chúng cung cấp API ánh xạ.

Hãy xem cách `Array.prototype.map ()` cho phép bạn trừu tượng kiểu dữ liệu từ tiện ích ánh xạ để làm cho `map ()` có thể sử dụng được với bất kỳ kiểu dữ liệu nào. Chúng ta sẽ tạo một ánh xạ `double ()` đơn giản, chỉ đơn giản là nhân bất kỳ giá trị nào được truyền vào với 2:

Điều gì sẽ xảy ra nếu chúng ta muốn hoạt động trên các mục tiêu trong một trò chơi để tăng gấp đôi số điểm mà họ giành được? Tất cả những gì chúng ta phải làm là tạo ra một thay đổi tinh tế cho hàm `double ()` mà chúng ta truyền vào hàm `map ()`, và mọi thứ vẫn hoạt động:

Khái niệm sử dụng các phép trừu tượng như hàm functors và các hàm bậc cao hơn để sử dụng các hàm tiện ích chung để thao tác với bất kỳ số lượng các kiểu dữ liệu khác nhau nào là quan trọng trong lập trình hướng chức năng. Bạn sẽ thấy một khái niệm tương tự được áp dụng trong [tất cả các cách khác nhau] [9].

> "A list expressed over time is a stream."

All you need to understand for now is that arrays and functors are not the only way this concept of containers and values in containers applies. For example, an array is just a list of things. A list expressed over time is a stream — so you can apply the same kinds of utilities to process streams of incoming events — something that you'll see a lot when you start building real software with FP.

### Declarative vs Imperative

Lập trình hướng chức năng là một mô hình declarative, có nghĩa là logic chương trình được biểu diễn mà không mô tả rõ ràng điều khiển luồng.

Các chương trình **Imperative** sử dụng các dòng code mô tả các bước cụ thể được sử dụng để đạt được kết quả mong muốn - điều khiển luồng **:Làm thế nào để làm việc**.

Các chương trình **Declarative** trừu tượng quá trình kiểm soát luồng, và thay vào đó chi tiêu các dòng mã mô tả **luồng dữ liệu: Phải làm gì**. Làm thế nào để được trừu tượng đi.

Ví dụ, ánh xạ **Imperative** này lấy một mảng các số và trả về một mảng mới với mỗi số nhân với 2:


Ánh xạ ** Declarative ** này cũng làm điều tương tự, nhưng tóm tắt điều khiển luồng bằng cách sử dụng tiện ích hàm `Array.prototype.map()`, cho phép bạn thể hiện rõ ràng luồng dữ liệu:

Code **Imperative** thường xuyên sử dụng các câu lệnh. **Câu lệnh** là một đoạn code thực hiện một số hành động. Ví dụ về các câu lệnh thường được sử dụng bao gồm `for`,`if`, `switch`,`throw`, v.v ...

**Declarative** dựa nhiều hơn vào biểu thức. **Biểu thức** là một đoạn mã đánh giá một số giá trị. Biểu thức thường là một số kết hợp của các cuộc gọi hàm, giá trị và toán tử được đánh giá để tạo ra giá trị kết quả.

Đây là tất cả các ví dụ về các biểu thức:
    
    
    2 * 2  
    doubleMap([2, 3, 4])  
    Math.max(4, 3, 2)

Thông thường trong mã, bạn sẽ thấy các biểu thức được gán cho một mã định danh, được trả về từ các hàm, hoặc được chuyển vào một hàm. Trước khi được chỉ định, trả về hoặc được thông qua, biểu thức được đánh giá đầu tiên và giá trị kết quả được sử dụng.

### Phần kết luận

Các dấu hiệu của lập trình hướng chức năng

* Các hàm thuần túy thay vì các ảnh hưởng phụ và trạng thái được chia sẻ
* Tính bất biến trên dữ liệu thay đổi
* Thành phần chức năng trên điều khiển lưu lượng bắt buộc
* Rất nhiều tiện ích chung, có thể tái sử dụng sử dụng các hàm bậc cao hơn để hành động trên nhiều loại dữ liệu thay vì các phương thức chỉ hoạt động trên dữ liệu được phân bổ của chúng
* Declarative chứ không phải là code bắt buộc (phải làm gì, hơn là làm thế nào để làm điều đó)
* Biểu thức trên báo cáo
* Các hàm chứa và hàm bậc cao hơn là tính đa hình


  
