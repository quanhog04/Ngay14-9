# Ngay14-9
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
