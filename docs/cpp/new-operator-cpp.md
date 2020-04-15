---
title: new 运算符 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367875"
---
# <a name="new-operator-c"></a>new 运算符 (C++)

从空闲存储为*类型名称*的对象或数组分配内存，并返回指向对象的适当类型非零指针。

> [!NOTE]
> Microsoft C++组件扩展程序支持**新**关键字添加可访问槽条目。 有关详细信息，请参阅[新插槽（vtable 中的新插槽）](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>语法

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>备注

如果不成功，新返回零或引发异常;如果失败，**则返回**零或引发异常。有关详细信息[，请参阅新建运算符和删除运算符](../cpp/new-and-delete-operators.md)。 可以通过编写自定义异常处理例程并将[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)运行时库函数与函数名称作为其参数来更改此默认行为。

有关如何在托管堆上创建对象的信息，请参阅[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)。

当**new**用于为C++类对象分配内存时，将在分配内存后调用对象的构造函数。

使用[delete](../cpp/delete-operator-cpp.md)运算符取消分配**与新运算符一**起分配的内存。

以下示例先分配然后释放一个二维字符数组，数组的大小为 `dim` x 10。 在分配多维数组时，除第一个维度之外的所有维度必须是计算结果为正值的常量表达式；最左侧的数组维度可以是计算结果为正值的任何表达式。 使用**新**运算符分配数组时，第一个维度可以是零 -**新**运算符返回唯一指针。

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*类型名称*不能包含**const、****易失性**、类声明或枚举声明。 因此，以下表达式是非法的：

```cpp
volatile char *vch = new volatile char[20];
```

**新**运算符不分配引用类型，因为它们不是对象。

**新**运算符不能用于分配函数，但可用于分配指向函数的指针。 下面的示例为返回整数的函数分配然后释放一个包含 7 个指针的数组。

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

如果使用运算符**new**而不提供任何额外的参数，并使用[/GX](../build/reference/gx-enable-exception-handling.md) [、/EHa](../build/reference/eh-exception-handling-model.md)或[/EHs](../build/reference/eh-exception-handling-model.md)选项进行编译，则编译器将生成代码，在构造函数引发异常时调用运算符**删除**。

下面的列表描述了**新的**语法元素：

*位置*<br/>
提供了一种传递其他参数的方法，如果重载**了 new**。

*类型名称*<br/>
指定要分配的类型；它可以是内置类型，也可以是用户定义的类型。 如果类型规范非常复杂，则可用括号将其括起来以强制实施绑定顺序。

*initializer*<br/>
为初始化对象提供值。 不能为数组指定初始值设定项。 仅当类具有默认构造函数时，**新**运算符才会创建对象的数组。

## <a name="example"></a>示例

下面的代码示例分配类 `CName` 的一个字符数组和一个对象，然后释放它们。

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>示例

如果使用**新**运算符的放置新窗体（除了分配大小之外带有参数的窗体），则如果构造函数引发异常，编译器不支持**delete**运算符的放置形式。 例如：

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>初始化使用 new 运算符分配的对象

**新**运算符的语法中包含可选的初始*化器*字段。 这样就可以使用用户定义的构造函数来初始化新对象。 有关如何初始化的详细信息，请参阅[初始化器](../cpp/initializers.md)。 以下示例说明了如何**与新运算符一**起使用初始化表达式：

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

在此示例中，使用**新**运算符分配`CheckingAcct`对象，但不指定默认初始化。 因此，调用了类的默认构造函数 `Acct()`。 然后，以相同的方式分配了对象 `SavingsAcct`，只不过将它显式初始化为 34.98。 由于 34.98 的类型为**双**，因此调用采用该类型参数的构造函数来处理初始化。 最后，将非类类型 `HowMuch` 初始化为 43.0。

如果对象是类类型，并且该类具有构造函数（如前面的示例所示），则只有在满足以下条件之一时，**新**运算符才能初始化该对象：

- 初始值设定项中提供的自变量与构造函数的自变量一致。

- 该类有一个默认构造函数（可在没有参数的情况下调用的构造函数）。

使用**新**运算符分配数组时，无法执行显式每个元素初始化;仅调用默认构造函数（如果存在）。 有关详细信息[，请参阅默认参数](../cpp/default-arguments.md)。

如果内存分配失败（**运算符 new**返回值 0），则不执行初始化。 这可防止尝试初始化不存在的数据。

与函数调用一样，未定义初始化表达式的计算顺序。 此外，您不应指望这些表达式能在执行内存分配前完全计算。 如果内存分配失败，**并且新**运算符返回零，则初始化器中的某些表达式可能无法完全计算。

## <a name="lifetime-of-objects-allocated-with-new"></a>使用 new 运算符分配的对象的生存期

退出使用**新**运算符分配的对象时，不会销毁它们的定义范围。 由于**新**运算符返回指向其分配的对象的指针，因此程序必须定义具有适当作用域的指针才能访问这些对象。 例如：

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

在上面的示例中，指针 `AnotherArray` 一旦超出范围，将无法再删除对象。

## <a name="how-new-works"></a>new 的工作方式

*分配表达式*（包含**新**运算符的表达式）执行三件事：

- 定位并保留要分配的对象的存储。 此阶段完成后，将分配正确的存储量，但它还不是对象。

- 初始化对象。 初始化完成后，将为成为对象的已分配存储显示足够的信息。

- 返回指向从*新类型名称*或*类型名称*派生的指针类型的对象的指针。 程序使用此指针来访问最近分配的对象。

**新**运算符调用函数**运算符 new**。 对于任何类型的数组，对于不是**类**、**结构**类型或**联合**类型的对象，调用全局函数 **：：运算符 new**，以分配存储。 类类型对象可以基于每个类定义自己的**运算符新的**静态成员函数。

当编译器遇到**新**运算符以分配**类型类型**的对象时，它将发出调用`type` **：： 运算符 new（sizeof）），**`type`**) )** 或者，如果没有定义用户定义的运算符**new（sizeof）** `type` **。** **operator new** 因此，**新**运算符可以为对象分配正确的内存量。

> [!NOTE]
> 运算符**new**的参数是`size_t`类型 。 \<此类型在直接.h>、malloc.h \<>、memory.h \<>、search.h \< \<>、stddef.h \<>、stdio.h>、stdlib.h \<>、string.h \<> 和\<time.h>中定义。

语法中的选项允许指定*放置*（请参阅[新运算符](../cpp/new-operator-cpp.md)的语法）。 *放置*参数只能用于**运算符 new**的用户定义的实现。它允许将额外的信息传递给**操作员新**。 如果类 T 具有新成员`T *TObject = new ( 0x0040 ) T;`运算符，否则`T *TObject = T::operator new( sizeof( T ), 0x0040 );`将`T *TObject = ::operator new( sizeof( T ), 0x0040 );`转换为 具有*放置字段的*表达式，例如将转换为 。

*放置*字段的初衷是允许在用户指定的地址分配与硬件相关的对象。

> [!NOTE]
> 尽管前面的示例在*放置*字段中只显示一个参数，但对于以这种方式传递给**新运算符**的额外参数数没有限制。

即使为类类型定义了**运算符 new，** 也可以使用此示例的形式使用全局运算符：

```cpp
T *TObject =::new TObject;
```

范围解析运算符 （`::`） 强制使用全局**新**运算符。

## <a name="see-also"></a>另请参阅

[具有一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[新建运算符和删除运算符](../cpp/new-and-delete-operators.md)
