### 1. Kế thừa (Inheritance)

#### Khái niệm Kế thừa trong C#
Kế thừa là một trong bốn tính chất quan trọng của lập trình hướng đối tượng (OOP). Kế thừa cho phép một lớp con (derived class) có thể kế thừa các thuộc tính và phương thức từ một lớp cha (base class). Điều này giúp tránh việc phải định nghĩa lại các thuộc tính và phương thức đã tồn tại ở lớp cha, từ đó giúp tái sử dụng mã nguồn và giảm thiểu sự trùng lặp.

#### Cách Kế thừa giúp tái sử dụng mã nguồn và giảm thiểu trùng lặp
- **Tái sử dụng mã nguồn**: Các phương thức và thuộc tính được định nghĩa trong lớp cha có thể được lớp con sử dụng mà không cần phải viết lại, giúp giảm thiểu mã trùng lặp.
- **Mở rộng chức năng**: Lớp con có thể bổ sung hoặc ghi đè (override) các phương thức của lớp cha để thực hiện các hành vi riêng, từ đó tạo ra sự linh hoạt và mở rộng chức năng mà vẫn giữ lại phần lớn mã của lớp cha.

#### Ví dụ về Kế thừa trong C#
```csharp
// Lớp cha (Base class)
class Animal
{
    public string Name { get; set; }
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

// Lớp con (Derived class)
class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}

// Sử dụng lớp Dog
class Program
{
    static void Main(string[] args)
    {
        Dog dog = new Dog();
        dog.Name = "Buddy"; // Sử dụng thuộc tính từ lớp cha
        dog.Eat(); // Sử dụng phương thức từ lớp cha
        dog.Bark(); // Sử dụng phương thức từ lớp con
    }
}
```
Trong ví dụ này, lớp `Dog` kế thừa lớp `Animal`, do đó nó có thể sử dụng các thuộc tính và phương thức của lớp `Animal` như `Name` và `Eat`.

---

### 2. Đa hình (Polymorphism)

#### Khái niệm Đa hình trong C#
Đa hình là khả năng cho phép các đối tượng khác nhau trả lời theo những cách khác nhau đối với cùng một thông điệp hay lời gọi phương thức. Đa hình giúp tăng tính linh hoạt và khả năng mở rộng của chương trình, giúp các lớp có thể thay đổi hành vi mà không ảnh hưởng đến các phần còn lại của hệ thống.

#### Phân biệt Đa hình tĩnh (Compile-time Polymorphism) và Đa hình động (Run-time Polymorphism)
- **Đa hình tĩnh (Compile-time Polymorphism)**: Xảy ra tại thời điểm biên dịch, thường thông qua phương thức nạp chồng (method overloading). Điều này có nghĩa là phương thức cùng tên nhưng khác nhau về số lượng hoặc kiểu tham số.
  
- **Đa hình động (Run-time Polymorphism)**: Xảy ra tại thời điểm chạy, thường thông qua phương thức ghi đè (method overriding). Đa hình động sử dụng từ khóa `virtual` trong lớp cha và `override` trong lớp con.

#### Ví dụ về Đa hình trong C#
1. **Method Overloading (Đa hình tĩnh)**:
```csharp
class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Calculator calc = new Calculator();
        Console.WriteLine(calc.Add(1, 2)); // Gọi phương thức Add với tham số int
        Console.WriteLine(calc.Add(1.5, 2.5)); // Gọi phương thức Add với tham số double
    }
}
```
Trong ví dụ này, phương thức `Add` được nạp chồng (overload) với hai phiên bản khác nhau, một phiên bản nhận tham số `int` và một phiên bản nhận tham số `double`.

2. **Method Overriding (Đa hình động)**:
```csharp
class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal is making a sound.");
    }
}

class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog is barking.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Animal animal = new Animal();
        Animal dog = new Dog();

        animal.Sound(); // Gọi phương thức Sound của lớp Animal
        dog.Sound(); // Gọi phương thức Sound của lớp Dog (ghi đè)
    }
}
```
Trong ví dụ này, phương thức `Sound` của lớp `Dog` ghi đè phương thức `Sound` của lớp `Animal`, giúp tạo ra đa hình động.

---

### 3. So sánh và Ứng dụng

#### So sánh giữa Kế thừa và Đa hình

| **Tiêu chí**       | **Kế thừa**                                  | **Đa hình**                                 |
|--------------------|----------------------------------------------|---------------------------------------------|
| **Định nghĩa**     | Quan hệ giữa lớp cha và lớp con, cho phép lớp con kế thừa thuộc tính và phương thức của lớp cha | Khả năng các đối tượng khác nhau phản hồi khác nhau với cùng một lời gọi phương thức |
| **Mục đích**       | Tái sử dụng mã nguồn, giảm trùng lặp         | Thay đổi hành vi của phương thức trong các lớp con |
| **Cách thức**      | Sử dụng từ khóa `: base class`               | Sử dụng `method overloading` (đa hình tĩnh) hoặc `method overriding` (đa hình động) |
| **Thời gian thực thi** | Biết trước tại thời điểm biên dịch        | Đa hình động được xác định tại thời điểm chạy |
| **Ví dụ**          | Lớp `Dog` kế thừa lớp `Animal`               | Phương thức `Sound()` được ghi đè trong lớp `Dog` |

#### Ứng dụng thực tế
- **Kế thừa**: Thường được sử dụng để tạo ra cấu trúc phân cấp cho các lớp trong hệ thống, ví dụ như các lớp quản lý sản phẩm, người dùng, hay các loại đối tượng có tính chất chung.
- **Đa hình**: Được sử dụng trong thiết kế hệ thống để các lớp con có thể tự động thay đổi hành vi mà không cần sửa đổi mã nguồn ở lớp cha, thường thấy trong các hệ thống mà yêu cầu mở rộng các chức năng theo thời gian như hệ thống thanh toán, quản lý người dùng.

#### Code ví dụ tổng hợp

```csharp
// Lớp cha (Base class)
class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal is making a sound.");
    }
}

// Lớp con (Derived class)
class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog is barking.");
    }
}

class Cat : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Cat is meowing.");
    }
}

// Sử dụng đa hình động và kế thừa
class Program
{
    static void Main(string[] args)
    {
        Animal myAnimal = new Animal();
        Animal myDog = new Dog();
        Animal myCat = new Cat();

        myAnimal.Sound(); // Output: Animal is making a sound.
        myDog.Sound();    // Output: Dog is barking.
        myCat.Sound();    // Output: Cat is meowing.
    }
}
```

Trong ví dụ này, lớp `Dog` và `Cat` kế thừa lớp `Animal` và ghi đè phương thức `Sound`, tạo ra đa hình động.
