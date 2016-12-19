---
title: "析构函数 (C++) | Microsoft Docs"
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
  - "~ 运算符, 指定析构函数"
  - "销毁对象, 析构函数"
  - "析构函数, 关于析构函数"
  - "析构函数, C++"
  - "对象 [C++], 销毁"
  - "Visual C++, 析构函数"
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 析构函数 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“析构函数”是构造函数的反向函数。  在销毁（释放）对象时将调用它们。  通过在类名前面放置一个波形符 \(`~`\) 将函数指定为类的析构函数。  例如，声明 `String` 类的析构函数：`~String()`。  
  
 在 \/clr 编译中，析构函数在释放托管和非托管资源方面发挥了特殊作用。  有关详细信息，请参阅[Visual C\+\+ 中的析构函数和终结器](../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
 析构函数通常用于在不再需要某个对象时“清理”此对象。  请考虑 `String` 类的以下声明：  
  
```  
// spec1_destructors.cpp  
#include <string.h>  
  
class String {  
public:  
   String( char *ch );  // Declare constructor  
   ~String();           //  and destructor.  
private:  
   char    *_text;  
   size_t  sizeOfText;  
};  
  
// Define the constructor.  
String::String( char *ch ) {  
   sizeOfText = strlen( ch ) + 1;  
  
   // Dynamically allocate the correct amount of memory.  
   _text = new char[ sizeOfText ];  
  
   // If the allocation succeeds, copy the initialization string.  
   if( _text )  
      strcpy_s( _text, sizeOfText, ch );  
}  
  
// Define the destructor.  
String::~String() {  
   // Deallocate the memory that was previously reserved  
   //  for this string.  
   if (_text)  
      delete[] _text;  
}  
  
int main() {  
   String str("The piper in the glen...");  
}  
```  
  
 在前面的示例中，析构函数 `String::~String` 使用 `delete` 运算符来动态释放为文本存储分配的空间。  
  
## 声明析构函数  
 析构函数是具有与类相同的名称但前面是波形符 \(`~`\) 的函数  
  
 该语法的第一种形式用于在类声明中声明或定义的析构函数；第二种形式用于在类声明的外部定义的析构函数。  
  
 多个规则管理析构函数的声明。  析构函数：  
  
-   不接受参数。  
  
-   无法指定任何返回类型（包括 `void`）。  
  
-   无法使用 `return` 语句返回值。  
  
-   无法声明为 **const**、`volatile` 或 **static**。  但是，可以为声明为 **const**、`volatile` 或 **static** 的对象的析构调用它们。  
  
-   可以声明为 **virtual**。  通过使用虚拟析构函数，无需知道对象的类型即可销毁对象 \- 使用虚函数机制调用该对象的正确析构函数。  请注意，析构函数也可以声明为抽象类的纯虚函数。  
  
## 使用构造函数  
 当下列事件之一发生时，将调用析构函数：  
  
-   使用 **delete** 运算符显式解除分配了使用 **new** 运算符分配的对象。  使用 **delete** 运算符解除分配对象时，将为“大多数派生对象”或为属于完整对象，但不是表示基类的子对象的对象释放内存。  此“大多数派生对象”解除分配一定仅对虚拟析构函数有效。  在类型信息与实际对象的基础类型不匹配的多重继承情况下，取消分配可能失败。  
  
-   具有块范围的本地（自动）对象超出范围。  
  
-   临时对象的生存期结束。  
  
-   程序结束，并且存在全局或静态对象。  
  
-   使用析构函数的完全限定名显式调用了析构函数。  （有关详细信息，请参阅[显式析构函数调用](../misc/explicit-destructor-calls.md)。）  
  
 前面的列表中所述的情况将确保所有对象均可通过用户定义的方法进行销毁。  
  
 如果基类或数据成员有一个可访问的析构函数，并且派生类未声明析构函数，则编译器将生成一个析构函数。  此编译器生成的析构函数将为派生类型的成员调用基类析构函数和析构函数。  默认析构函数是公共的。  （有关可访问性的详细信息，请参阅[基类的访问修饰符](../misc/access-specifiers-for-base-classes.md)。）  
  
 析构函数可以随意调用类成员函数和访问类成员数据。  从析构函数调用虚函数时，调用的函数是当前正在销毁的类的函数。  （有关详细信息，请参阅[析构函数的顺序](../misc/order-of-destruction.md)。）  
  
 析构函数的使用有两个限制。  第一个限制是您无法采用析构函数的地址。  第二个是派生类不会继承其基类的析构函数。  相反，如前所释，它们始终重写基类的析构函数。  
  
## 析构的顺序  
 当对象超出范围或被删除时，其完整析构中的事件序列如下所示：  
  
1.  将调用该类的析构函数，并且会执行该析构函数的主体。  
  
2.  按照非静态成员对象的析构函数在类声明中的显示顺序的相反顺序调用这些函数。  用于这些成员的构造的可选成员优化列表不影响构造或析构的顺序。  （有关初始化成员的详细信息，请参阅[初始化基和成员](http://msdn.microsoft.com/zh-cn/2f71377e-2b6b-49da-9a26-18e9b40226a1)。）  
  
3.  非虚拟基类的析构函数以声明的相反顺序被调用。  
  
4.  虚拟基类的析构函数以声明的相反顺序被调用。  
  
```  
// order_of_destruction.cpp  
#include <stdio.h>  
  
struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };  
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };  
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };  
  
struct B1      { ~B1() { printf("B1 dtor\n"); } };  
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };  
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };  
  
int main() {  
   A1 * a = new A3;  
   delete a;  
   printf("\n");  
  
   B1 * b = new B3;  
   delete b;  
   printf("\n");  
  
   B3 * b2 = new B3;  
   delete b2;  
}  
  
Output: A3 dtor  
A2 dtor  
A1 dtor  
  
B1 dtor  
  
B3 dtor  
B2 dtor  
B1 dtor  
  
```  
  
### 虚拟基类  
 按照与虚拟基类在定向非循环图形中显示的顺序的相反顺序调用这些虚拟基类的析构函数（深度优先、从左到右、后序遍历）。  下图描述了继承关系图。  
  
 ![显示虚拟基类的继承图](../cpp/media/vc392j1.png "vc392J1")  
演示虚拟基类的继承关系图  
  
 下面列出了图中显示的类的类头。  
  
```  
class A  
class B  
class C : virtual public A, virtual public B  
class D : virtual public A, virtual public B  
class E : public C, public D, virtual public B  
```  
  
 为了确定 `E` 类型的对象的虚拟基类的析构顺序，编译器将通过应用以下算法来生成列表：  
  
1.  向左遍历关系图，并从关系图中的最深点开始（在此示例中，为 `E`）。  
  
2.  执行左移遍历，直到访问了所有节点。  记下当前节点的名称。  
  
3.  重新访问上一个节点（向下并向右）以查明要记住的节点是否为虚拟基类。  
  
4.  如果记住的节点是虚拟基类，请浏览列表以查看是否已将其输入。  如果它不是虚拟基类，则将其忽略。  
  
5.  如果记住的节点尚未包含在列表中，请将其添加到列表的底部。  
  
6.  向上遍历关系图并沿下一个路径向右遍历。  
  
7.  转到步骤 2。  
  
8.  在用完最后一个向上路径时，请记下当前节点的名称。  
  
9. 转到步骤 3。  
  
10. 继续执行此过程，直到底部节点再次成为当前节点。  
  
 因此，对于 `E` 类，析构顺序为：  
  
1.  非虚拟基类 `E`。  
  
2.  非虚拟基类 `D`。  
  
3.  非虚拟基类 `C`。  
  
4.  虚拟基类 `B`。  
  
5.  虚拟基类 `A`。  
  
 此过程将生成唯一项的有序列表。  任何类名均不会出现两次。  在构造列表后，将以相反的顺序遍历该列表，并且将调用列表中每个类（从最后一个到第一个）的析构函数。  
  
 如果某个类中的构造函数或析构函数依赖于要先创建或保留更长时间的另一个组件（例如，如果 `A` 的析构函数（上图中所示）依赖于执行其代码时仍存在 `B`），则构造或析构的顺序特别重要，反之亦然。  
  
 继承关系图中各个类之间的这种相互依赖项本质上是危险的，因为稍后派生类可以更改最左边的路径，从而更改构造和析构的顺序。  
  
### 非虚拟基类  
 按照相反的顺序（按此顺序声明基类名称）调用非虚拟基类的析构函数。  考虑下列类声明：  
  
```  
class MultInherit : public Base1, public Base2  
...  
```  
  
 在前面的示例中，先于 `Base2` 的析构函数调用 `Base1` 的析构函数。  
  
## 显式析构函数调用  
 很少需要显式调用析构函数。  但是，对置于绝对地址的对象进行清理会很有用。  这些对象通常使用采用位置参数的用户定义的 **new** 运算符进行分配。  **delete** 运算符不能释放该内存，因为它不是从自由存储区分配的（有关详细信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)）。  但是，对析构函数的调用可以执行相应的清理。  若要显式调用 `s` 类的对象 `String` 的析构函数，请使用下列语句之一：  
  
```  
s.String::~String();     // Nonvirtual call  
ps->String::~String();   // Nonvirtual call  
  
s.~String();       // Virtual call  
ps->~String();     // Virtual call  
```  
  
 可以使用对前面显示的析构函数的显式调用的表示法，无论类型是否定义了析构函数。  这允许您进行此类显式调用，而无需了解是否为此类型定义了析构函数。  显式调用析构函数，其中未定义的析构函数无效。  
  
## 请参阅  
 [特殊成员函数](../misc/special-member-functions-cpp.md)