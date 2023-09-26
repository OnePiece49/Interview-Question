# Interview-Question

1. OOP

- Encapsulation: Là cách ta đóng gói dữ liệu và phương thức thành 1 class, điều này giúp dữ liệu được ẩn đi bằng cách sử dụng các access modifier như `open, public, internal,fileprivate, private.`
- Abstraction: Là cách ta hiển thị dữ liệu và phương thức mong muốn của đối tượng và ẩn đi các logic phức tạp bên trong. Điều này làm cho code dễ đọc, dễ maintain và sử dụng trong tương lai.
- Inheritance: Trong swift thì cho phép 1 class kế thừa 1 class khác. Trong swift chỉ cho phép đơn kế thừa, còn để đạt được trạng thái mong muốn là đa kế thừa thì ta có thể sử dụng protocol
- Polymorphism: Với cùng 1 method ở superclass, các subclass khác nhau có thể ovveride method đó để triển khai các cách khác nhau.

2. So sánh Class và Struct

Giống nhau:
- Đều có thể định nghĩa các thuộc tính để lưu giá trị, định nghĩa các method để thực thi các chức năng, định nghĩa các hàm khởi tạo init. Đều có thể kế thừa protocol. Và có thể được extend bởi extensions

Khác nhau:
- Điểm khác biệt lớn nhất là Class là reference Type còn Struct và Enum là Value Type. Vì vậy Class có cơ chế Reference counting cho phép nhiều hơn 1 reference refer tới 1 class instance. Và Class có hàm deinit, struct thì ko có  
- Điểm khác biệt thứ 2 là Class cho phép kế thừa còn Struct thì không.


3. Protocol và delegate là gì

Protocol: định nghĩa 1 blueprint cho các methods, propertie. Protocol có thể được adopted bởi class, struct, enum. Bất kì kiểu dữ liệu nào mà đáp ứng những methors và properties đó thì được gọi là đã comform protocol. 

Ta thường dùng protocol cho các trường hợp như:

- Khi ta muốn đảm bảo 1 kiểu dữ liệu phải có đủ các methods và properties mong muốn.
- Delegate
- Đa kế thừa

Trong swift, delegate là 1 design pattern cho phép 1 đối tượng gửi message tới 1 đối tượng khác khi có 1 sự kiện xảy ra. Khi sử dụng delegate, ta khai báo nó với kiểu tham chiếu weak để tránh retail cycle. Delegate là kiểu quan hệ 1 1

4. GCD

Trước khi nhắc đến `GCD` thì ta cần phải nhắc tới `Queue`. Queue là 1 hàng đợi block code để đợi các Thread thực thi. `GCD` là 1 low level API được cung cấp để quản lý Queue, công việc chính của GCD là: Tạo Queue, Đưa các block code vào trong Queue. GCD cho phép ta tạo 2 loại Queue:
- Serial Queue: Các block code được thực thi lần lượt
- ConcurrentQueue: Các block code được thực thi đồng thời.

5. Có bao nhiêu mức Access Control trong Swift? Hãy liệt kê chúng theo thứ tự giảm dần 

Trong swift có 5 mức Access Control đó là: `Open, Public, Internal, fileprivate, private`

- `Open Access`: Thì class đó có thể được truy cập và kế thừa từ mọi source file mà import module này, các phương thức hoặc thuộc tính của class Open có thể được Override từ các source file đó. 
- `Public Access`: Thì class Public đó chỉ có thể được truy cập từ các source file mà import module này, chứ ko thể kế thừa hoặc override các thuộc tính các class public.
- `Internal Access`: Chỉ các entity trong Module đó mới có quyền truy cập vào class Internal
- `Fileprivate Access`: Chỉ các entity trong file đó mới có quyền truy cập vào fileprivate class
- `Private Access`: Chỉ có thể được truy cập ở bên trong class khai báo nó.

6. Quản lý bộ nhớ trong IOS thế nào
Swift sử dụng `ARC` để theo dõi và quản lý memory. `ARC` sẽ theo dõi số lượng refercence tới instance. Khi số lượng reference về 0, vùng nhớ đó sẽ được thu hồi.

ARC là 1 thuộc tính của trình biên dịch, thay vì người dùng phải tự mình thu hồi các vùng nhớ ko sử dụng thì compiler sẽ làm nó 

7. Strong and Weak

Strong Reference là 1 kiểu tham chiếu được sử dụng để giữ đối tượng trong bộ nhớ. Weak Reference không làm tăng . Weak thường được sử dụng để tránh retain cycles

8. IOS Application Life Cycle

Các trạng thái của 1 IOS Application: `Not Running, In Active, Active, Backgound, Suspended.`
- `Not Running:` Khi chúng ta mở máy lên thì chưa có ứng dụng nào được chạy, và tất cả các App ở trạng thái `Not Running`.
- `Active`: Sau khi ta nhấn vào biểu tượng App trên điện thoại chúng ta, thì App chúng ta vào trạng thái `InActive`(Kiểu lúc nó mới Lauch thì ra màn hình trắng, và ko thể tương tác với UI của App vì nó chưa được load xong UI 😊)) rồi về trạng thái `Active` và chạy trên `Foregroud`, lúc này người dùng có thể tương tác với giao diện của App. Khi App đã được mở sẵn nhưng chạy trên Backgroud, thì khi người dùng mở lại App thì App đang từ trạng `Background` sẽ về trạng `InActive` rồi về `Active`.
- `In-Active`: Trong các trường hợp như có các cuộc gọi hoặc tin nhắn tới, thì lúc này App rơi vào trạng thái `In-Active`. Lúc này App vẫn chạy trên `ForeGround`, nhưng không nhận bất kì sự kiện tương tác nào của người dùng.
- `Background`: Khi người dùng nhấn home để về màn hình chính hoặc sử dụng 1 App khác thì App hiện tại sẽ chạy dưới background nhưng vẫn thực thi code. Khi người dùng nhấn home, App từ trạng thái Active sẽ về In-Active rồi về trạng thái Backgroud
- `Suspended:` App chạy dưới `Backgroud` nhưng không thực thi code.

![](Images/app_lifeCycle.png)

9. Mô hình MVC và MVVM

MVC gồm 3 thành phần là Model, View, Controller:
- `Model`: Đại diện cho dữ liệu, chứa thông tin và login của ứng dụng ? `Có chứa login ko ???`
- `View`: Đại diện cho giao diện của người dùng của ứng dụng, hiển thị dữ liệu từ model, cho phép người dùng tương tác với ứng dụng
- `Controller`: Đại diện cho login điều khiển của ứng dụng, là cấu nối giữa model và view, xử lý các yêu cầu từ view sau đó update view và model. 

Mô hình MVVM gồm 3 thành phần là `Model, View và ViewModel`:
- View: Chỉ thực hiện nhưng công việc liên quan đến giao diện: Như là lấy dữ liệu từ viewModel và sau đó hiển thị thông tin.
- ViewModel: Nhận thông tin từ ViewController, xử lý tất cả các thông tin này, sau đó gửi lại cho VC
- Model: Đại diện cho dữ liệu của ứng dụng

Flow dữ liệu của MVVM:
- Đầu tiên 1 ViewController sẽ có 1 tham chiến tới ViewModel
- ViewController sẽ nhận ã vài hành động của user, và sau đó sẽ gọi tới ViewModel
- ViewModel sẽ request APIService, sau đó trả response ngược lại cho viewModel
- Khi viewModel nhận response, ViewModel sẽ thông báo cho ViewController thông qua Binding
- View sẽ update UI với Data vừa nhận được

10. Closure

Closure là một block code mà có thể được sử dụng trong code. Closure có thể capture và store value và reference bất kì 1 biến hay 1 constant nào từ context mà nó được defined. 
- [Capturing Values](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/closures/#Capturing-Values): 

Closure có thể capture và store reference bất kì 1 biến hay 1 constant nào từ context mà nó được defined. Closure có thể refer và modify giá trị của biến trong body của nó ngay cả khi phạm vi ban đầu(`original scope`) mà defined biến đó không còn tồn tại.

Closures Are Reference Types.

```swift
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}


var incrementByTen = makeIncrementer(forIncrement: 10)
```

Ta thấy func `makeIncrementer` return lại 1 closure nên biến `incre` là 1 closure. Mà closure là 1 `reference type`, nên `incre` sẽ tham chiếu tới closure `incrementer`. Mà `runningTotal` `capturing value` 2 biến `runningTotal` và `amount`, dẫn đến

```swift
incrementByTen()
// returns a value of 10
incrementByTen()
// returns a value of 20
incrementByTen()
// returns a value of 30
```

Ta thấy ko phải return full 10, mà return 10, 20, 30.

- Từ khóa `escaping`: Một closure được gọi là `escape` khi closure đó được pass vào function như là 1 parameter của function đó và được gọi khi function đó đã return.

Có 2 trường hợp mà ta cần khi viết closure:
- Khi ta cần lưu closure đó bên ngoài function:

```swift
var completionHandlers: [() -> Void] = []
func someFunctionWithEscapingClosure(completionHandler: @escaping () -> Void) {
    completionHandlers.append(completionHandler)
}
```

-  Khi fetch API

11. Enum là gì

`Enumeration` hay Enum còn được gọi là kiểu liệt kê, nó khai báo một nhóm các giá trị liên quan với nhau, nhằm tạo sự tường minh trong lập trình cũng như tính toán và xử lý.
- Là kiểu tham trị
- Không có tính thừa kế.

Enumeration case có thể chứa giá trị liên kết (`associated values`). Mục đích là chứa thêm thông tin của enum case. 

```swift
enum People {
    case viet(Int, Int)
    case long(Int)
}

var hello = People.viet(123, 555555)

switch hello {
    case let .viet(siu, aa):
        print("\(siu) and \(aa)")
    case .long(let qq):
        print("qq \(qq)")
}
```

Khi để `case let` thì các biến bên trong không được khai báo `let` nữa. Còn khi chỉ khai báo `case` thì tất cả các biến bên trong cần khai báo `let` như ví dụ trên.

Ta hay sử dụng `associated values` với kiểu dữ liệu `Result`. `Result` được triển khai như 1 enum có 2 case là `success` và `failure`. `failure` bắt buộc phải là 1 kiểu dữ liệu mà comform kiểu `Error`.

```swift
enum NetworkError: Error {
    case badUrl(String)
    case badRequest(String)
}

var failure: Result<Int, NetworkError> = .failure(.badUrl("URL is invinvalid"))
var success: Result<Int, NetworkError> = .success(123123)

switch failure {      //Testing with switch success
    case let .success(value):
        print(value)
    case let .failure(error):
        switch error {
            case let .badUrl(description):
                print("error: \(description)")
            case let .badRequest(description):
                print(description)
        }
}
```

Đôi khi làm việc với enum ta cần làm việc với `rawValue`

- Raw value là giá trị mặc định được đưa ra của enumeration case, có cùng kiểu dữ liệu với enumeration. 
- Đối với kiểu string hoặc integer, Swift tự động gán giá trị raw value cho enum case nếu case đó không được gán giá trị mặc định.

```swift
// #1
enum Suit1: String {
    case spades = "Spades"
    case hearts = "Hearts"
    case diamonds = "Diamonds"
    case clubs = "Clubs"
}

enum Suit2: String {
    case spades
    case hearts
    case diamonds
    case clubs
}

enum Suit3: Int {
    case spades = 1
    case hearts
    case diamonds
    case clubs
}

var suit2 = Suit2(rawValue: "diamonds")
var suit3  = Suit3(rawValue: 4)

print(Suit1.spades.rawValue)
print(Suit2.spades.rawValue)
print(suit2)
print(suit3)
```

12. HTTP

Http là 1 protocol mà cho phép truyền dữ liệu qua internet. Dữ liệu có thể là: text, video, âm thanh. Để có thể nhận được resource từ server, client gửi 1 bản tin `http request` tới server, server sẽ gửi lại 1 `http response`.

Cấu trúc của 1 bản tin `http request` là: 

![](Images/request.webp)

Cấu trúc của 1 bản tin `http response` là: 

![](Images/response.webp)

- Get: Được sử dụng để requet 1 tài nguyên từ server
- Post: Được sử dụng để tạo mới hoặc thêm tài nguyên (resource) vào server. HTTP Post thường có body, và các thành phần header như: content-type, content-length.
- Put: Được sử dụng để modify resource, Put sẽ update toàn bộ data mà được truyền vào phần body, nếu ko có tài nguyên nào ứng với request, nó sẽ khởi tạo tài nguyên mới.
- Patch: Được sử dụng để update 1 phần resource.
- Delete: Được sử dụng để xóa resource.

So sánh các phương thức:

- Post và Put: Mỗi lần gọi Post thì sẽ tạo ra 1 tài nguyên mới, dẫn đến gọi nhiều lần Post sẽ sinh ra nhiều tài nguyên. Còn với Put thì cái này chỉ sửa resource đã có, dẫn đến khi gọi nhiều lần cũng chỉ ra cùng 1 kết quả.
- Put và Patch: Với Put sẽ tạo mới tài nguyên nếu chưa có tài nguyên, hoặc sẽ sửa lại toàn bộ tài nguyên. Còn với Patch chỉ update 1 resource.

13. RESTFULApi

`RESTFULApi` là 1 Api mà thỏa mãn được các rang buộc của kiến trúc Rest. Các rang buộc đó là:

- Sử dụng kiến trúc client-server 
- Stateless: Nghĩa là các thông tin của client sẽ không lưu trữ lại tại server, mỗi request là độc lập
- Uniform Interface: Mỗi 1 resource chỉ có 1 identifier(URI)
- Cachable: Liên quan tới khả năng lưu lại và sử dụng lại responses của server. Điều này làm cải thiện hiệu năng ứng dụng, Khi nào server response lại header là cachable thì thông tin đó mới có thể được lưu lại.
- Layer system: client có thể kết nối tới bên ủy quyền trung gian, và vẫn có thể nhận được response từ server. Chúng ta có thể thiết kế nhiều server.
- Code on demand: Server có thể custom các chức năng của client bằng cách gửi 1 đoạn code tới client. VD khi user register 1 form, brosewr có thể hightlights lỗi luôn nhờ server.

14. Collection Types

Swift cung cấp cho ta 3 kiểu `collection types` chính đó là `arrays, sets, và dictionaries`.

- `Array`: là mảng chứa các giá trị có cùng kiểu dữ liệu với nhau. Các giá trị này có thể suất hiện nhiều lần ở các vị trí khác nhau. Chỉ số đầu tiên của một Array là 0.

Khởi tạo Array:

```swift
var someInts: [Int] = []
var threeDoubles = Array(repeating: 0.0, count: 3)
var shoppingList = ["Eggs", "Milk"]

for (index, value) in shoppingList.enumerated() {
    print("Item \(index + 1): \(value)")
}
```

- `Set`: Set lưu các giá trị khác nhau với cùng kiểu dữ liệu mà không có sự sắp xếp nào. Ta sử dụng `Set` thay vì `Array` khi vị trí của các phần tử không quan trọng, hoặc khi muốn đảm bảo các phần tử chỉ xuất hiện 1 lần.



15. Hashable

Trong Swift, `Hashable` là 1 protocol cung cấp cho ta thuộc tính `hashValue`. `hashValue` được sử dụng để compare 2 instances. Để sử dụng `hashValue`, đầu tiên ta cần comform `Hashavle` như sau([Hashable](https://www.programiz.com/swift-programming/hashable)):

```swift
struct Employee: Hashable {
    var name: String
    var salary: Int
}
```

```swift
let obj1 = Employee(name: "Sabby", salary: 40000)
let obj2 = Employee(name: "Cathy", salary: 30000)

print("Different hash value: ")
print(obj1.hashValue)
print(obj2.hashValue)

// initialize two objects with same property values 
let obj3 = Employee(name: "Lanny", salary: 50000)
let obj4 = Employee(name: "Lanny", salary: 50000)

print("\nSame hash value: ")
print(obj3.hashValue)
print(obj4.hashValue)
```

Output:

```swift
Different hash value: 
3934953678767833906
4997634560615333199

Same hash value: 
1588129438168529318
1588129438168529318
```








