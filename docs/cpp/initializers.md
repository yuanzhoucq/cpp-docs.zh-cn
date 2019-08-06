---
title: 初始值设定项
ms.date: 07/29/2019
description: 如何在中C++初始化类、结构、数组和基础类型。
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: fd926177dd7540d8dc1e8512e9f17e20a0b8238c
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661617"
---
# <a name="initializers"></a>初始值设定项

初始值设定项可指定变量的初始值。 你可以在以下上下文中初始化变量：

- 在变量的定义中：

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- 作为函数的一个参数：

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- 作为函数的返回值：

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

初始值设定项可以采用以下形式：

- 括号中的表达式（表达式的逗号分隔列表）：

    ```cpp
    Point p1(1, 2);
    ```

- 等号后跟表达式：

    ```cpp
    string s = "hello";
    ```

- 括号内的初始值设定项列表。 该列表可能为空，或可能包含一组列表，如下面的示例所示：

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>初始化类型

初始化有若干类型，可能出现在程序执行的不同点。 不同的初始化类型并不是相互排斥的。例如，列表初始化可触发值初始化，在其他情况中，它可以触发聚合初始化。

### <a name="zero-initialization"></a>零初始化

零初始化是指将变量设置为隐式转换为该类型的零值：

- 数值变量初始化为 0（或 0.0、0.0000000000 等）。

- Char 变量将初始化为`'\0'`。

- 将指针初始化为**nullptr**。

- 数组、 [POD](../standard-library/is-pod-class.md)类、结构和联合的成员被初始化为零值。

零初始化在不同的时间执行：

- 在程序启动时，对具有静态持续时间的所有已命名变量进行初始化。 这些变量可以稍后再次初始化。

- 值初始化期间，对使用空大括号初始化的标量类型和 POD 类类型进行初始化。

- 对只有部分成员初始化的数组进行初始化。

以下是零初始化的一些示例：

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a>默认初始化

类、结构和联合的默认初始化是具有默认构造函数的初始化。 可以不带初始化表达式或用**new**关键字调用默认构造函数:

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

如果类、结构或联合没有默认构造函数，则编译器将发出错误。

如果定义标量变量时不使用初始化表达式，则进行默认初始化。 它们的值是不确定的。

```cpp
int i1;
float f;
char c;
```

如果定义数组时不使用初始化表达式，则进行默认初始化。 数组进行默认初始化时，其成员将进行默认初始化并具有不确定的值，如以下示例所示：

```cpp
int int_arr[3];
```

如果数组成员没有默认构造函数，则编译器将发出错误。

#### <a name="default-initialization-of-constant-variables"></a>常量变量的默认初始化

常量变量必须与初始值设定项一起声明。 如果它们是标量类型，则会导致编译器错误，而如果是具有默认构造函数的类类型，则将导致警告：

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>静态变量的默认初始化

如果静态变量的声明中没有初始值设定项，则初始化为 0（隐式转换为该类型）。

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

有关全局静态对象的初始化的详细信息, 请参阅[其他启动注意事项](../cpp/additional-startup-considerations.md)。

### <a name="value-initialization"></a>值初始化

值初始化发生在以下情况下：

- 使用空大括号初始化来初始化已命名值

- 使用空圆括号或大括号初始化匿名临时对象

- 使用**新**关键字加空括号或大括号初始化对象

值初始化执行以下操作：

- 对于至少有一个公共构造函数的类，将调用默认构造函数

- 对于没有声明构造函数的非联合类，该对象进行零初始化，并调用默认构造函数

- 对于数组，每个元素都进行值初始化

- 在其他所有情况下，变量进行零初始化

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>复制初始化

复制初始化是指使用一个不同的对象来初始化另一个对象。 在以下情况下，它会发生：

- 使用等号初始化变量

- 参数被传递给函数

- 从函数返回对象

- 引发或捕获异常

- 使用等号初始化非静态数据成员

- 在聚合初始化期间通过复制初始化来初始化类、结构和联合成员。 有关示例, 请参阅[聚合初始化](#agginit)。

下面的代码显示复制初始化的几个示例：

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

复制初始化不能调用显式构造函数。

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

有时，如果类的复制构造函数被删除或不可访问，复制初始化将导致编译器错误。

### <a name="direct-initialization"></a>直接初始化

直接初始化是使用（非空）大括号或圆括号的初始化。 不同于复制初始化，它可以调用显式构造函数。 在以下情况下，它会发生：

- 使用非空大括号或圆括号初始化变量

- 使用**新**关键字和非空大括号或圆括号初始化变量

- 用**static_cast**初始化变量

- 在构造函数中，使用初始值设定项列表初始化基类和非静态成员

- lambda 表达式中捕获的变量的副本中

以下代码显示直接初始化的一些示例：

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>列表初始化

使用大括号内的初始值设定项列表初始化变量时，将发生列表初始化。 大括号内的初始值设定项列表可在以下情况中使用：

- 初始化变量

- 使用**new**关键字初始化类

- 从函数返回对象

- 自变量传递给函数

- 直接初始化中的自变量之一

- 在非静态数据成员的初始值设定项中

- 在构造函数初始值设定项列表中

以下代码显示了列表初始化的一些示例：

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a>聚合初始化

聚合初始化是针对数组或类类型（通常为结构或联合）的一种列表初始化形式：

- 没有私有或受保护成员

- 没有用户提供的构造函数，显式默认或删除的构造函数除外

- 没有基类

- 没有虚拟成员函数

> [!NOTE]
> <!--conformance note-->在 Visual Studio 2015 及更早版本中, 不允许聚合使用非静态成员的大括号或等号初始值设定项。 此限制已在 c + + 14 标准中删除, 并在 Visual Studio 2017 中实现。

聚合初始值设定项包括含等号或不含等号的括号内的初始化列表，如以下示例所示：

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

您应看到以下输出：

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> 在聚合初始化期间声明但未显式初始化的数组成员将进行零初始化, 如`myArr3`上面所示。

#### <a name="initializing-unions-and-structs"></a>初始化联合和结构

如果联合没有构造函数，你可以使用单个值（或使用联合的另一个实例）对其初始化。 该值用于初始化第一个非静态字段。 结构初始化与其不同，其初始值设定项中的第一个值用于初始化第一个字段，第二个值用于初始化第二个字段，依此类推。 比较以下示例中联合和结构的初始化：

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>初始化包含聚合的聚合

聚合类型可包含其他聚合类型，例如数组的数组、结构的数组等。 这些类型使用嵌套的大括号组进行初始化，例如：

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>引用初始化

引用类型的变量必须使用引用类型派生自的类型的对象进行初始化，或使用可转换为引用类型派生自的类型的类型的对象进行初始化。 例如:

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

使用临时对象初始化引用的唯一方式是初始化常量临时对象。 初始化后，引用类型变量始终指向同一对象；不能将它修改为指向另一个对象。

尽管语法可以相同，但引用类型变量的引用和引用类型变量的赋值在语义上不同。 在前面的示例中，更改 `iVar` 和 `lVar` 的赋值看起来像初始化，但它们有不同的效果。 初始化指定引用类型变量指向的对象；赋值通过引用向引用目标对象赋值。

由于将引用类型的自变量传递给函数或从函数返回引用类型的值都是初始化，因此会正确初始化函数的形式自变量，就像它们是返回的引用一样。

只有在下列声明中才能在没有初始值设定项的情况下声明引用类型变量：

- 函数声明（原型）。 例如:

    ```cpp
    int func( int& );
    ```

- 函数返回类型声明。 例如:

    ```cpp
    int& func( int& );
    ```

- 引用类型类成员的声明。 例如:

    ```cpp
    class c {public:   int& i;};
    ```

- 显式指定为**extern**的变量的声明。 例如:

    ```cpp
    extern int& iVal;
    ```

初始化引用类型变量时，编译器将使用下图中所示的决策关系图，在创建对对象的引用或创建引用所指向的临时对象之间做出选择。

![引用类型的初始化决策图](../cpp/media/vc38s71.gif "引用类型的初始化决策图") <br/>
引用类型的初始化决策图

对**可变**类型的引用 (声明为**易失性** *typename* <strong>&</strong> *标识符*) 可以使用相同类型的**可变**对象或未声明为**volatile**的对象进行初始化. 但不能用该类型的**const**对象对其进行初始化。 同样, 可使用相同类型的**const**对象 (或具有到该类型的转换或对象的任何类型的任何内容) 初始化对**const**类型的引用 (声明为**const** *typename* <strong>&</strong> *标识符*)。尚未声明为**const**的。) 但是, 它们不能用该类型的**可变**对象进行初始化。

不带**const**或**volatile**关键字限定的引用只能用声明为**const**和**volatile**的对象进行初始化。

### <a name="initialization-of-external-variables"></a>外部变量的初始化

自动、静态和外部变量的声明可包含初始值设定项。 但是, 仅当变量未声明为**extern**时, 外部变量的声明才能包含初始值设定项。