---
title: 作为值类型的 C++ 类
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246025"
---
# <a name="c-classes-as-value-types"></a>作为值类型的 C++ 类

C++ 类是由默认值类型。 它们可以指定为引用类型，这将启用多态行为以支持面向对象的编程。 值类型有时从内存和布局控制的角度进行查看，而对于多态目的，引用类型是关于基类和虚函数的。 默认情况下，值类型为复制，这意味着始终有一个复制构造函数和一个复制赋值运算符。 对于引用类型，请将类设为不可复制（禁用复制构造函数和复制赋值运算符），并使用支持其所需多态性的虚拟析构函数。 值类型也涉及内容，在复制这些内容时，始终向您授予两个独立的值，这些值可以单独修改。 引用类型是关于标识的，它是哪种类型的对象？ 出于此原因，"引用类型" 也称为 "多态类型"。

如果确实需要类似于引用的类型（基类、虚函数），则需要显式禁用复制，如以下代码中的 `MyRefType` 类所示。

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

编译上述代码将导致以下错误：

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>值类型和移动效率

由于新的复制优化，因此避免了复制分配开销。 例如，当你在字符串矢量的中间插入一个字符串时，将不会重新分配任何复制开销，只会产生一个移动，即使它导致矢量本身增长。 这也适用于其他操作，例如在两个非常大的对象上执行添加操作。 如何启用这些值操作优化？ 在某些 C++ 编译器，编译器将启用这为你隐式一样可以由编译器自动生成复制构造函数。 但是，在C++中，你的类将需要 "选择加入" 才能在类定义中声明分配和构造函数。 这是通过在相应的成员函数声明中使用双与号（& &）右值引用以及定义移动构造函数和移动赋值方法来完成的。  还需要插入正确的代码来 "盗取探讨" 源对象。

你如何决定是否需要启用移动？ 如果你已经知道你需要启用了复制构造，则可能想要使其比深层复制更便宜。 但是，如果您知道您需要移动支持，则不一定意味着要启用复制。 后一种情况称为 "仅移动类型"。 标准库中已 `unique_ptr`的示例。 请注意，旧 `auto_ptr` 已被弃用，并且已被完全 `unique_ptr` 替换，因为在以前版本的C++中缺少移动语义支持。

使用移动语义可以返回按值或 insert in 中间。 移动是副本的优化。 需要将堆分配作为一种解决方法。 请看下面的伪代码：

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>为适当的值类型启用移动

对于类似于值的类，其中移动可以比深层复制更便宜，启用移动构造并移动分配以提高效率。 请看下面的伪代码：

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

如果启用 "复制构造/分配"，则如果其比深层复制更便宜，还可以启用 "移动构造/分配"。

某些*非值*类型是只移动的，例如当无法克隆资源时，只转移所有权。 示例：`unique_ptr`。

## <a name="see-also"></a>另请参阅

[C++类型系统](../cpp/cpp-type-system-modern-cpp.md)<br/>
[欢迎返回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
