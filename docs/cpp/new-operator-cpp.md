---
title: "new 运算符 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new 关键字 [C++]"
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# new 运算符 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从自由存储为 *type\-name* 的对象或对象数组分配内存，并将已适当分类的非零指针返回到对象。  
  
> [!NOTE]
>  Microsoft C\+\+ 组件扩展为 `new` 关键字提供支持以添加 vtable 槽条目。  有关详细信息，请参阅[新的 \(在 vtable 的新槽\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## 语法  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## 备注  
 如果不成功，则 **new** 将返回零或引发异常；有关详细信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)。  通过编写自定义异常处理例程并调用 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) 运行库函数（以您的函数名称作为其参数），可以更改此默认行为。  
  
 有关如何在托管堆上创建对象的信息，请参阅 [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
 使用 **new** 为 C\+\+ 类对象分配内存时，将在分配内存后调用对象的构造函数。  
  
 使用 [delete](../cpp/delete-operator-cpp.md) 运算符可解除分配使用 **new** 运算符分配的内存。  
  
 以下示例先分配然后释放一个二维字符数组，数组的大小为 `dim` x 10。  在分配多维数组时，除第一个维度之外的所有维度必须是计算结果为正值的常量表达式；最左侧的数组维度可以是计算结果为正值的任何表达式。  在使用 **new** 运算符分配数组时，第一个维度可为零 \- **new** 运算符将返回一个唯一指针。  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *type\-name* 不能包含 **const**、`volatile`、类声明或枚举声明。  因此，以下表达式是非法的：  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 **new** 运算符不会分配引用类型，因为这些类型不是对象。  
  
 **new** 运算符无法用于分配函数，但可用于分配指向函数的指针。  下面的示例为返回整数的函数分配然后释放一个包含 7 个指针的数组。  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 如果使用不带任何额外参数的 **new** 运算符，并用 [\/GX](../build/reference/gx-enable-exception-handling.md)、[\/EHa](../build/reference/eh-exception-handling-model.md) 或 [\/EHs](../build/reference/eh-exception-handling-model.md) 选项进行编译，则编译器将在构造函数引发异常时生成代码来调用运算符 **delete**。  
  
 以下列表描述了 **new** 的语法元素：  
  
 *placement*  
 如果重载 **new**，则提供了一种传递附加参数的方式。  
  
 *type\-name*  
 指定要分配的类型；它可以是内置类型，也可以是用户定义的类型。  如果类型规范非常复杂，则可用括号将其括起来以强制实施绑定顺序。  
  
 *initializer*  
 为初始化对象提供值。  不能为数组指定初始值设定项。  仅当类具有默认构造函数时，**new** 运算符才会创建对象的数组。  
  
## 示例  
 下面的代码示例分配类 `CName` 的一个字符数组和一个对象，然后释放它们。  
  
```  
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
  
## 示例  
 如果使用 **new** 运算符的放置新形式（带有参数和分配大小的形式），如果构造函数引发异常，则编译器不支持 **delete** 运算符的放置形式。  例如:  
  
```  
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
  
## 初始化使用 new 运算符分配的对象  
 可选的 *initializer* 字段包含在 **new** 运算符的语法中。  这样就可以使用用户定义的构造函数来初始化新对象。  有关如何执行初始化的详细信息，请参阅[初始值设定项](../cpp/initializers.md)。  以下示例演示如何将初始化表达式与 **new** 运算符一起使用：  
  
```  
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
  
 在此示例中，使用 `CheckingAcct`new 运算符分配了  **对象，但未指定默认初始化。** 因此，调用了类的默认构造函数 `Acct()`。  然后，以相同的方式分配了对象 `SavingsAcct`，只不过将它显式初始化为 34.98。  由于 34.98 是类型 **double**，因此调用了采用该类型的参数的构造函数来处理初始化。  最后，将非类类型 `HowMuch` 初始化为 43.0。  
  
 如果对象是类类型，并且该类具有构造函数（如前面的示例所示），则仅当满足以下条件之一时，**new** 运算符才能初始化该对象：  
  
-   初始值设定项中提供的参数与构造函数的参数一致。  
  
-   该类有一个默认构造函数（可在没有参数的情况下调用的构造函数）。  
  
 访问控制和二义性控制根据`operator new`多义性和[使用特殊成员函数的初始化](http://msdn.microsoft.com/zh-cn/0b399cab-40a7-4e79-9278-05f40139a0e1)中所述的规则对 [和构造函数执行。](http://msdn.microsoft.com/zh-cn/82223d73-64cb-4923-b678-78f9568ff3ca)  
  
 在使用 **new** 运算符分配数组时，无法对每个元素执行显式初始化；只调用了默认构造函数（如果有）。  有关详细信息，请参阅[默认参数](../cpp/default-arguments.md)。  
  
 如果内存分配失败（`operator new` 的返回值为 0），则不执行初始化。  这可防止尝试初始化不存在的数据。  
  
 与函数调用一样，未定义初始化表达式的计算顺序。  此外，您不应指望这些表达式能在执行内存分配前完全计算。  如果内存分配失败，并且 **new** 运算符返回零，则可能不会完全计算初始值设定项中的某些表达式。  
  
## 使用 new 运算符分配的对象的生存期  
 在退出分配有 **new** 运算符的对象的定义范围时，将不会销毁这些对象。  由于 **new** 运算符将返回指向其所分配的对象的指针，因此程序必须使用合适的范围定义指针才能访问这些对象。  例如:  
  
```  
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
  
## new 的工作方式  
 *allocation\-expression*（包含 **new** 运算符的表达式）执行三类操作：  
  
-   定位并保留要分配的对象的存储。  此阶段完成后，将分配正确的存储量，但它还不是对象。  
  
-   初始化对象。  初始化完成后，将为成为对象的已分配存储显示足够的信息。  
  
-   返回指向派生自 *new\-type\-name* 或 *type\-name* 的指针类型的对象的指针。  程序使用此指针来访问最近分配的对象。  
  
 **new** 运算符调用函数 `operator new`。  对于任何类型的数组以及不属于 **class**、`struct` 或 **union** 类型的对象，调用全局函数 **::operator new** 来分配存储。  类类型对象可基于每个类定义其自己的 `operator new` 静态成员函数。  
  
 当编译器遇到用于分配 `type` 类型的对象的 **new** 运算符时，它将发出对 `type`**::operator new\( sizeof\(** `type` **\) \)** 的调用；或者，如果不存在用户定义的 `operator new`，则调用 **::operator new\( sizeof\(** `type` **\) \)**。  因此，**new** 运算符可以为对象分配正确的内存量。  
  
> [!NOTE]
>  `operator new` 的参数属于 **size\_t** 类型。  在 DIRECT.H、MALLOC.H、MEMORY.H、SEARCH.H、STDDEF.H、STDIO.H、STDLIB.H、STRING.H 和 TIME.H 中定义此类型。  
  
 该语法中的选项允许 *placement* 的规范（请参阅 [new 运算符](../cpp/new-operator-cpp.md)的语法）。  *placement* 参数仅可用于 `operator new` 的用户定义的实现；它允许将额外信息传递给 `operator new`。  如果类 T 具有成员运算符 new，则将具有 *placement* 字段的表达式（例如，`T *TObject = new ( 0x0040 ) T;`）转换为 `T *TObject = T::operator new( sizeof( T ), 0x0040 );`；否则将其转换为 `T *TObject = ::operator new( sizeof( T ), 0x0040 );`。  
  
 *placement* 字段的原始用途是允许在用户指定的地址分配硬件相关对象。  
  
> [!NOTE]
>  虽然上面的示例仅显示 *placement* 字段内的一个参数，但不限制可通过此方法传递给 `operator new` 的额外参数的数目。  
  
 即使已为类类型定义 `operator new`，也可以采用此示例的形式来使用全局运算符：  
  
```  
T *TObject =::new TObject;  
```  
  
 范围解析运算符 \(`::`\) 强制使用全局 **new** 运算符。  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [operator new 函数](../misc/operator-new-function.md)