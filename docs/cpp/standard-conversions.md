---
title: "标准转换 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "转换, 标准"
  - "L-values"
  - "标准转换, 类别"
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 标准转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 语言定义其基础类型之间的转换。  它还定义指针、引用和指向成员的指针派生类型的转换。  这些转换称为“标准转换。”（有关类型、标准类型和派生类型的详细信息，请参阅[类型](http://msdn.microsoft.com/zh-cn/6882ee83-ea32-4373-8d57-c3efbbc15af0)。）  
  
 本节讨论下列标准转换：  
  
-   [整型提升](../misc/integral-promotions.md)  
  
-   [整型转换](../misc/integral-conversions.md)  
  
-   [浮点转换](../misc/floating-conversions.md)  
  
-   [浮点转换和整型转换](../misc/floating-and-integral-conversions.md)  
  
-   [算术转换](../misc/arithmetic-conversions.md)  
  
-   [指针转换](../misc/pointer-conversions-cpp.md)  
  
-   [引用转换](../misc/reference-conversions.md)  
  
-   [指向成员的指针转换](../misc/pointer-to-member-conversions.md)  
  
    > [!NOTE]
    >  用户定义的类型可指定其自己的转换。  [构造函数](../cpp/constructors-cpp.md)和[转换](../cpp/user-defined-type-conversions-cpp.md)中介绍了用户定义的类型的转换。  
  
 以下代码将导致转换（本例中为整型提升）：  
  
```  
long  lnum1, lnum2;  
int   inum;  
  
// inum promoted to type long prior to assignment.  
lnum1 = inum;  
  
// inum promoted to type long prior to multiplication.  
lnum2 = inum * lnum2;  
```  
  
> [!NOTE]
>  仅当转换生成引用类型时，其结果才为左值。  例如，声明为  
  
```  
operator int&()  
```  
  
> [!NOTE]
>  的用户定义的转换将返回引用，并且是左值。  但是，声明为  
  
```  
operator int()  
```  
  
> [!NOTE]
>  的转换将返回对象，但不是左值。  
  
## 整型提升  
 整数类型的对象可以转换为另一个更宽的整数类型（即，可表示更大的一组值的类型）。  这种扩展类型的转换称为“整型提升”。 利用整型提升，您可以在可使用其他整数类型的任何位置将以下项用于表达式：  
  
-   `char` 和 `short int` 类型的对象、文本和常量  
  
-   枚举类型  
  
-   `int` 位域  
  
-   枚举器  
  
 C\+\+ 提升是“值保留”。 即，提升后的值一定与提升前的值相同。  在值保留提升中，如果 `char` 可以表示原始类型的完整范围，较短的整数类型的对象（如 `int` 类型的位域或对象）将提升到 `int` 类型。  如果 `int` 无法表示完整范围的值，该对象将提升到 `unsigned int` 类型。  尽管此策略与 ANSI C 中使用的相同，但值保留转换不保留对象的“符号”。  
  
 值保留提升和保留符号的提升通常会生成相同的结果。  但是，如果提升的对象是以下项之一，它们可能生成不同的结果：  
  
-   **\/**、`%`、`/=`、`%=`、**\<**、**\<\=**、**\>** 或 **\>\=** 的操作数  
  
     这些运算符依赖于用于确定结果的符号。  因此，当值保留和符号保留提升应用于这些操作数时，它们将生成不同的结果。  
  
-   **\>\>** 或 **\>\>\=** 的左操作数  
  
     当执行移位运算时，这些运算符会区别对待有符号的数量和无符号的数量。  对于有符号的数量，将数量右移会导致符号位传播到空出的位位置。  对于无符号的数量，空出的位位置将由零填充。  
  
-   重载函数的参数，或重载运算符的操作数（取决于该操作数的用于参数匹配的类型的符号）。  （有关定义重载运算符的详细信息，请参阅[重载运算符](../cpp/operator-overloading.md)。）  
  
## 整型转换  
 整型转换在整型之间执行。  整型包括 `char`、`int` 和 **long**（以及这些类型的 **short**、**signed** 和 `unsigned` 版本）。  
  
 **有符号转换为无符号**  
  
 有符号整数类型的对象可以转换为对应的无符号类型。  当这些转换发生时，实际位模式不会更改；但是，数据的解释会更改。  考虑此代码：  
  
```  
// conve__pluslang_Converting_Signed_to_Unsigned.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
int main()  
{  
    short  i = -3;  
    unsigned short u;  
  
    cout << (u = i) << "\n";  
}  
// Output: 65533  
  
```  
  
 在前面的示例中，`signed short` `i` 被定义和初始化为负数。  表达式 `(u = i)` 导致 `i` 在为  **赋值前转换为 `u`unsigned short**。  
  
 **无符号转换为有符号**  
  
 无符号整数类型的对象可以转换为对应的有符号类型。  但是，如果无符号对象的值在有符号类型表示的范围之外，则此类转换可能导致数据错误解释，如以下示例所示：  
  
```  
// conve__pluslang_Converting_Unsigned_to_Signed.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
int main()  
{  
 short  i;  
 unsigned short u = 65533;  
  
 cout << (i = u) << "\n";  
}  
//Output: -3  
```  
  
 在前面的示例中，`u` 是一个 `unsigned` **short** 整数对象，必须将其转换为有符号的数量来计算表达式 `(i = u)`。  由于其值无法在 `signed short` 中正确表示，因此数据被错误解释。  
  
## 浮点转换  
 浮动类型的对象可以安全地转换为更精确的浮点类型，也就是说，转换不会导致基数丢失。  例如，从 **float** 到 **double** 或从 **double** 到 `long double` 的转换是安全的，并且值保持不变。  
  
 如果浮点类型的对象位于低精度类型可表示的范围中，则还可转换为该类型。  （有关浮点类型的范围，请参阅[浮点限制](../cpp/floating-limits.md)。） 如果原始值不能精确地表示，则可将其转换为下一更高或更低的可表示值。  如果此类值不存在，则结果是不确定的。  请看下面的示例：  
  
```  
cout << (float)1E300 << endl;  
```  
  
 类型 **float** 可表示的最大值为 3.402823466E38 \- 比 1E300 小很多。  因此，该数字将转换为无穷大，结果为 1.\#INF。  
  
## 整型和浮点型之间的转换  
 某些表达式可能导致浮点型的对象转换为整型，反之亦然。  当整型对象转换为浮点型且无法正确表示原始值时，结果要么是下一个较大的可表示值，要么是下一个较小的可表示值。  
  
 当浮点型的对象转换为整型时，小数部分将被截断。  转换过程中不会进行舍入。  截断意味着，数字 1.3 将转换为 1，–1.3 将转换为 –1。  
  
## 算术转换  
 很多二元运算符（在[带二元运算符的表达式](../cpp/expressions-with-binary-operators.md)中有讨论）会导致操作数转换并以相同的方式产生结果。  这些运算符导致转换的方式称为“常用算术转换”。 不同本机类型的操作数的算术转换按下表所示的方式执行。  Typedef 类型的行为方式基于其基础本机类型。  
  
### 类型转换的条件  
  
|满足的条件|转换|  
|-----------|--------|  
|其中一个操作数是 **long double** 类型。|另一个操作数将转换为 **long double** 类型。|  
|未满足上述条件，并且其中一个操作数是 **double** 类型。|另一个操作数将转换为 **double** 类型。|  
|未满足上述条件，并且其中一个操作数是 **float** 类型。|另一个操作数将转换为 **float** 类型。|  
|未满足上述条件（没有任何一个操作数属于浮动类型）。|整型提升按以下方式对操作数执行：<br /><br /> -   如果其中一个操作数是 `unsigned` **long** 类型，则另一个操作数将转换为 `unsigned long` 类型。<br />-   如果未满足上述条件，并且其中一个操作数是 **long** 类型，另一个操作数是 `unsigned` `int` 类型，则两个操作数都将转换为 `unsigned long` 类型。<br />-   如果未满足上述两个条件，并且其中一个操作数是 **long** 类型，则另一个操作数将转换为 **long** 类型。<br />-   如果未满足上述三个条件，并且其中一个操作数是 `unsigned int` 类型，则另一个操作数将转换为 `unsigned int` 类型。<br />-   如果上述条件均未满足，则两个操作数都将转换为 `int` 类型。|  
  
 以下代码演示了上表中所述的转换规则：  
  
```  
// arithmetic_conversions.cpp  
double dVal;  
float fVal;  
int iVal;  
unsigned long ulVal;  
  
int main() {  
   // iVal converted to unsigned long  
   // result of multiplication converted to double  
   dVal = iVal * ulVal;  
  
   // ulVal converted to float  
   // result of addition converted to double  
   dVal = ulVal + fVal;  
}  
```  
  
 上面的示例中的第一个语句显示了两个整数类型 `iVal` 和 `ulVal` 的相乘。  满足的条件是两个操作数都不是浮动类型，并且一个操作数是 `unsigned int` 类型。  因此，另一个操作数 \(`iVal`\) 将转换为 `unsigned int` 类型。  结果将分配给 `dVal`。  满足的条件是一个操作数是 **double** 类型；因此，相乘的 `unsigned int` 结果将转换为 **double** 类型。  
  
 前面的示例中的第二个语句显示了 **float** 类型 `fVal` 和整数类型 `ulVal` 的相加。  `ulVal` 变量将转换为 **float** 类型（表中的第三个条件）。  相加的结果将转换为 **double** 类型（表中的第二个条件）并分配给 `dVal`。  
  
## 指针转换  
 在赋值、初始化、比较和其他表达式中，可以转换指针。  
  
### 指向类的指针  
 在两种情况下，指向类的指针可转换为指向基类的指针。  
  
 第一种情况是指定的基类可访问且转换是明确的。  （有关不明确的基类引用的详细信息，请参阅[多个基类](../cpp/multiple-base-classes.md)。）  
  
 基类是否可访问取决于派生中使用的继承的类型。  考虑下图中阐释的继承。  
  
 ![显示基类的可访问性的继承图](../cpp/media/vc38xa1.png "vc38XA1")  
阐明基类可访问性的继承关系图  
  
 下表显示针对该图阐释的情况的基类可访问性。  
  
### 基类可访问性  
  
|函数的类型|派生|从<br /><br /> B\* 到 A\* 的转换是否合法？|  
|-----------|--------|------------------------------|  
|外部（非类范围）函数|Private|No|  
||Protected|No|  
||Public|是|  
|B 成员函数（在 B 范围内）|Private|是|  
||Protected|是|  
||Public|是|  
|C 成员函数（在 C 范围内）|Private|No|  
||Protected|是|  
||Public|是|  
  
 第二种情况是，在您使用显式类型转换时，指向类的指针可转换为指向基类的指针。  （有关显性类型转换的详细信息，请参阅[使用显式类型转换的表达式](http://msdn.microsoft.com/zh-cn/060ad6b4-9592-4f3e-8509-a20ac84a85ae)。）  
  
 此类转换的结果是指向完全由基类描述的对象部分（即“子对象”）的指针。  
  
 以下代码定义了两个类（即 `A` 和 `B`），其中 `B` 派生自 `A`。  （有关继承的详细信息，请参阅[派生类](../cpp/inheritance-cpp.md)。） 然后定义 `bObject`、类型 `B` 的对象和两个指向该对象的指针（`pA` 和 `pB`）。  
  
```  
// conve__pluslang_Pointers_to_Classes.cpp  
// C2039 expected  
class A  
{  
public:  
    int AComponent;  
    int AMemberFunc();  
};  
  
class B : public A  
{  
public:  
    int BComponent;  
    int BMemberFunc();  
};  
int main()  
{  
   B bObject;  
   A *pA = &bObject;  
   B *pB = &bObject;  
  
   pA->AMemberFunc();   // OK in class A  
   pB->AMemberFunc();   // OK: inherited from class A  
   pA->BMemberFunc();   // Error: not in class A  
}  
```  
  
 指针 `pA` 的类型为 `A *`，它可解释为“指向类型 `A` 的对象的指针”。 `bObject` `(` 的成员（如 `BComponent` 和 `BMemberFunc`）对类型 `B` 是唯一的，并且无法通过 `pA` 进行访问。  `pA` 指针只允许访问类 `A` 中定义的对象的那些特性（成员函数和数据）。  
  
### 指向函数的指针  
 如果类型 **void \*** 足以保留指向函数的指针，则该指针可以转换为 **void \*** 类型。  
  
### 指向 void 的指针  
 指向 `void` 类型的指针可以转换为指向其他任何类型的指针，但仅适合于显式类型转换（与在 C 中的情况不同）。  （有关类型转换的详细信息，请参阅[带显式类型转换的表达式](http://msdn.microsoft.com/zh-cn/060ad6b4-9592-4f3e-8509-a20ac84a85ae)。） 指向任何类型的指针可以隐式转换为指向类型 `void` 的指针。指向类型的不完整对象的指针可以转换为指向 `void`（隐式）和 back（显式）的指针。  此类转换的结果与原始指针的值相等。  对象被视为是不完整的（如果已声明对象），但未提供足够多的可用信息，无法确定其大小或基类。  
  
 指向不是 **const** 或 `volatile` 的任何对象的指针可以隐式转换为 **void \*** 类型的指针。  
  
### 固定和可变指针  
 C\+\+ 将不会应用从 **const** 或 `volatile` 类型到不是 **const** 或 `volatile` 类型的标准转换。  但是，任何类型的转换都可以用显式类型强制转换指定（包括不安全的转换）。  
  
> [!NOTE]
>  指向成员的 C\+\+ 指针（指向静态成员的指针除外）与常规指针不同，二者具有不同的标准转换。  指向静态成员的指针是普通指针，且与普通指针具有相同的转换。  （请参阅[\(NOTINBUILD\) Directly Derived Types](http://msdn.microsoft.com/zh-cn/d2d611d1-dbff-4fb4-9858-e1572544f5c3)以获取详细信息。）  
  
### null 指针转换  
 计算结果为零的整数常量表达式，或到某个指针类型的此类表达式强制转换，将转换为称为“null 指针”的指针。 此指针与指向任何有效对象或函数的指针比较的结果肯定不会相等（指向基对象的指针除外，此类指针可以有相同的偏移量并且仍指向不同的对象）。  
  
 在 C\+\+11 中， [nullptr](../cpp/nullptr.md) 类型应优先于 C 样式 null 指针。  
  
### 指针表达式转换  
 带数组类型的所有表达式都可以转换为同一类型的指针。  转换的结果是指向第一个数组元素的指针。  下面的示例演示了这样的转换：  
  
```  
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 生成返回特定类型的函数的表达式将转换为指向返回该类型的函数的指针，以下情况除外：  
  
-   表达式用作 address\-of 运算符 \(**&**\) 的操作数。  
  
-   表达式用作到 function\-call 运算符的操作数。  
  
## 引用转换  
 对类的引用可在以下情况下转换为对基类的引用：  
  
-   指定的基类是可访问的（如[指向类的指针](../misc/pointers-to-classes.md)中定义的那样）。  
  
-   转换是明确的。  （有关不明确的基类引用的详细信息，请参阅[多个基类](../cpp/multiple-base-classes.md)。）  
  
 转换的结果为指向表示基类的子对象的指针。  
  
## 指向成员的指针  
 指向可在赋值、初始化、比较和其他语句中转换的类成员的指针。  本节描述以下指向成员的指针转换：  
  
## 指向基类成员的指针  
 当满足以下条件时，指向基类的成员的指针可以转换为指向派生自基类的类的成员的指针：  
  
-   从指向派生类的指针到基类指针的反向转换可以访问。  
  
-   派生类并非以虚拟方式从基类继承。  
  
 当左操作数是指向成员的指针时，右操作数必须是 pointer\-to\-member 类型或计算结果为 0 的常量表达式。  此赋值仅在以下情况下有效：  
  
-   右操作数是指向与左操作数相同的类的成员的指针。  
  
-   左操作数是指向以公共但不明确的方式派生自右操作数的类的成员的指针。  
  
## 整数常量转换  
 计算结果为零的整数常量表达式将转换为名为“null 指针”的指针。 此指针与指向任何有效对象或函数的指针比较的结果肯定不会相等（指向基对象的指针除外，此类指针可以有相同的偏移量并且仍指向不同的对象）。  
  
 以下代码演示了指向类 `i` 中的成员 `A` 的指针的定义。  指针 `pai` 将初始化为 0，因此是 null 指针。  
  
```  
// conve__pluslang_Integral_Constant_Expressions.cpp  
class A  
{  
public:  
 int i;  
};  
  
int A::*pai = 0;  
  
int main()  
{  
}  
```  
  
## 请参阅  
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)