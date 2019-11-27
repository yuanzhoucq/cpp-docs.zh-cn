---
title: 标准转换
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: c51a5ea5aaabb27babb9e4cd355721742088d31e
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998902"
---
# <a name="standard-conversions"></a>标准转换

C++ 语言定义其基础类型之间的转换。 它还定义指针、引用和指向成员的指针派生类型的转换。 这些转换称为*标准转换*。

本节讨论下列标准转换：

- 整型提升

- 整型转换

- 浮点转换

- 浮点转换和整型转换

- 算术转换

- 指针转换

- 引用转换

- 指向成员的指针转换

  > [!NOTE]
  > 用户定义的类型可指定其自己的转换。 [构造函数](../cpp/constructors-cpp.md)和[转换](../cpp/user-defined-type-conversions-cpp.md)中介绍了用户定义类型的转换。

以下代码将导致转换（本例中为整型提升）：

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

仅当转换生成引用类型时，其结果才为左值。 例如，声明为 `operator int&()` 的用户定义的转换将返回引用，并且是左值。 但是，声明为 `operator int()` 的转换将返回对象，而不是左值。

## <a name="integral-promotions"></a>整型提升

整数类型的对象可以转换为另一个更宽的整型类型，即可以表示较大值集的类型。 这种扩大类型的转换被称为*整型提升*。 使用整型提升时，可以在表达式中使用以下类型，只要可以使用其他整型类型：

- **Char**和**short**类型的对象、文本和常量

- 枚举类型

- **int**位域

- 枚举数

C++提升为 "值保留"，可保证提升后的值与提升前的值相同。 在值保留提升的情况下，如果**int**可以表示原始类型的完整范围，则较短整型类型的对象（如位域或**char**类型的对象）将提升为**int**类型。 如果**int**无法表示值的完整范围，则对象将提升为类型**无符号整数**。 尽管此策略与标准 C 所使用的策略相同，但值保留转换不保留对象的 "符号"。

值保留提升和保留符号的提升通常会生成相同的结果。 但是，如果升级的对象显示为，它们可能会产生不同的结果：

- `/`、`%`、`/=`、`%=`、`<`、`<=`、`>`或 `>=` 的操作数

   这些运算符依赖于用于确定结果的符号。 当应用于这些操作数时，值保留和签署保存会产生不同的结果。

- `>>` 或 `>>=` 的左操作数

   在移位操作中，这些运算符会以不同的方式处理签名和未签名的数量。 对于有符号数量，右移操作会将符号位传播到空出的位位置，而空出的位位置则以无符号的数量填充。

- 重载函数的参数或重载运算符的操作数，它依赖于参数匹配的操作数类型的符号。 有关定义重载运算符的详细信息，请参阅[重载运算符](../cpp/operator-overloading.md)。

## <a name="integral-conversions"></a>整型转换

*整型转换*是整型之间的转换。 整数类型包括**char**、 **short** （或**short int**）、 **int**、 **long**和**long**。 这些类型可以使用**带符号**或**无符号**进行限定，**无**符号可用作**无符号 int**的简写形式。

### <a name="signed-to-unsigned"></a>有符号转换为无符号

有符号整数类型的对象可以转换为对应的无符号类型。 发生这些转换时，实际的位模式不会更改。 但是，数据的解释会发生变化。 考虑此代码：

```cpp
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

在前面的示例中，定义了一个**带符号的 short**、`i`，并将其初始化为负数。 表达式 `(u = i)` 会导致在分配到 `u`之前 `i` 转换为**无符号短**。

### <a name="unsigned-to-signed"></a>无符号转换为有符号

无符号整数类型的对象可以转换为对应的有符号类型。 但是，如果无符号值不在已签名类型的可表示范围内，则结果将不具有正确的值，如以下示例中所示：

```cpp
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

在前面的示例中，`u` 是**无符号的短**整型对象，必须将其转换为有符号的数量，才能 `(i = u)`计算表达式。 因为它的值不能以**有符号的短格式**正确表示，所以数据会被错误解释为。

## <a name="floating-point-conversions"></a>浮点转换

浮动类型的对象可以安全地转换为更精确的浮点类型，也就是说，转换不会导致基数丢失。 例如，从**float**到**double**或从**double**到**long double**的转换是安全的，并且值不变。

如果浮动类型的对象位于由该类型表示的范围内，则它也可以转换为不太精确的类型。 （请参阅浮动类型范围的[浮动限制](../cpp/floating-limits.md)。）如果原始值不能准确地表示，则可以将其转换为下一个较高的值或下一个较小的可表示值。 如果不存在这样的值，则结果是不确定的。 请看下面的示例：

```cpp
cout << (float)1E300 << endl;
```

类型**float**可表示的最大值为 3.402823466 e 38-比1E300 小得多。 因此，该数字将转换为无穷，结果为 "inf"。

## <a name="conversions-between-integral-and-floating-point-types"></a>整型和浮点型之间的转换

某些表达式可能导致浮点型的对象转换为整型，反之亦然。 当整数类型的对象转换为浮点类型并且原始值不能完全表示时，结果是下一个较高的或下一个较小的可表示值。

当浮动类型的对象转换为整型时，小数部分将被*截断*或舍入到零。 数字（如1.3）转换为1，-1.3 转换为-1。 如果截断后的值高于最大的可表示值，或小于最小的可表示值，则结果是不确定的。

## <a name="arithmetic-conversions"></a>算术转换

许多二进制运算符（在[带二元运算符的表达式](../cpp/expressions-with-binary-operators.md)中讨论）会导致操作数转换，并以相同的方式生成结果。 这些运算符导致的转换称为*常用算术转换*。 按照下表中所示，完成具有不同本机类型的操作数的算术转换。 Typedef 类型的行为方式基于其基础本机类型。

### <a name="conditions-for-type-conversion"></a>类型转换的条件

|满足的条件|转换|
|--------------------|----------------|
|任一操作数的类型为**long double**。|其他操作数转换为**long double**类型。|
|不满足上述条件，并且任一操作数为**double**类型。|其他操作数转换为**double**类型。|
|前面的条件未满足，其中一个操作数的类型为**float**。|其他操作数转换为**float**类型。|
|未满足上述条件（没有任何一个操作数属于浮动类型）。|操作数获取整型升级，如下所示：<br /><br />-如果一个操作数的类型为**无符号 long**，则另一个操作数将转换为**无符号长**型类型。<br />-如果未满足上述条件，并且其中一个操作数的类型为**long** ，而另一个操作数的类型为**无符号 int**，则两个操作数都转换为**无符号的 long**类型。<br />-如果不满足上述两个条件，并且任一操作数的类型为**long**，则将另一个操作数转换为**long**类型。<br />-如果不满足上述三个条件，并且其中一个操作数的类型为**无符号 int**，则将另一个操作数转换为类型**无符号整数**。<br />-如果未满足上述任何条件，则两个操作数都将转换为**int**类型。|

以下代码演示了上表中所述的转换规则：

```cpp
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

上面的示例中的第一个语句显示了两个整数类型 `iVal` 和 `ulVal` 的相乘。 满足的条件是，这两个操作数都不是浮点型，一个操作数的类型为**无符号整数**。因此，另一个操作数 `iVal`将转换为类型**无符号整数**。然后，将结果分配给 `dVal`。 这里满足的条件是：一个操作数为**double**类型，因此乘法的**无符号 int**结果将转换为**double**类型。

前面的示例中的第二个语句显示了**float**和整型类型的加法： `fVal` 和 `ulVal`。 `ulVal` 变量将转换为**float**类型（表中的第三个条件）。 加法的结果转换为**double**类型（表中的第二个条件）并分配给 `dVal`。

## <a name="pointer-conversions"></a>指针转换

在赋值、初始化、比较和其他表达式中，可以转换指针。

### <a name="pointer-to-classes"></a>指向类的指针

在两种情况下，指向类的指针可转换为指向基类的指针。

第一种情况是指定的基类可访问且转换是明确的。 有关不明确的基类引用的详细信息，请参阅[多个基类](../cpp/multiple-base-classes.md)。

基类是否可访问取决于派生中使用的继承的类型。 考虑下图中阐释的继承。

![显示&#45;基类可访问性](../cpp/media/vc38xa1.gif "&#45;")的继承关系图显示基类辅助功能 <br/>
阐明基类可访问性的继承关系图

下表显示针对该图阐释的情况的基类可访问性。

|函数的类型|派生|从<br /><br /> B *\* 法律？|
|----------------------|----------------|-------------------------------------------|
|外部（非类范围）函数|专用|是|
||受保护|是|
||公共|是|
|B 成员函数（在 B 范围内）|专用|是|
||受保护|是|
||公共|是|
|C 成员函数（在 C 范围内）|专用|是|
||受保护|是|
||公共|是|

第二种情况是，在您使用显式类型转换时，指向类的指针可转换为指向基类的指针。 有关显式类型转换的详细信息，请参阅[显式类型转换运算符](explicit-type-conversion-operator-parens.md)。

此类转换的结果是指向子*对象的指针，该*对象是由基类完全描述的对象部分。

以下代码定义了两个类（即 `A` 和 `B`），其中 `B` 派生自 `A`。 （有关继承的详细信息，请参阅[派生类](../cpp/inheritance-cpp.md)。）然后，它定义 `bObject`、`B`类型的对象和指向该对象的两个指针（`pA` 和 `pB`）。

```cpp
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

指针 `pA` 的类型为 `A *`，它可解释为“指向类型 `A` 的对象的指针”。 `bObject` 的成员（例如 `BComponent` 和 `BMemberFunc`）对于类型 `B` 是唯一的，因此不能通过 `pA`访问。 `pA` 指针只允许访问类 `A` 中定义的对象的那些特性（成员函数和数据）。

### <a name="pointer-to-function"></a>指向函数的指针

指向函数的指针可以转换为类型 `void *`，如果类型 `void *` 足够大，无法保存该指针。

### <a name="pointer-to-void"></a>指向 void 的指针

指向**void**类型的指针可以转换为指向任何其他类型的指针，但仅适用于显式类型转换（与在 C 中不同）。 指向任何类型的指针可以隐式转换为指向**void**类型的指针。 指向类型的不完整对象的指针可以转换为指向**void** （隐式）和 back （显式）的指针。 此类转换的结果与原始指针的值相等。 如果对象已声明，但没有足够的信息可用于确定其大小或基类，则认为该对象是不完整的。

指向非**const**或**volatile**的任何对象的指针可以隐式转换为类型 `void *`的指针。

### <a name="const-and-volatile-pointers"></a>固定和可变指针

C++不提供从**常量**或**可变**类型到不是**常量**或**可变**类型的标准转换。 但是，任何类型的转换都可以用显式类型强制转换指定（包括不安全的转换）。

> [!NOTE]
> C++指向成员的指针（指向静态成员的指针除外）与普通指针不同，并且不具有相同的标准转换。 指向静态成员的指针是普通指针，且与普通指针具有相同的转换。

### <a name="null-pointer-conversions"></a>null 指针转换

计算结果为零的整数常量表达式，或者转换为指针类型的表达式，转换为名为*null 指针*的指针。 此指针始终将与指向任意有效对象或函数的指针进行比较。 异常是指向基于对象的指针，它们可以具有相同的偏移量，并且仍指向不同的对象。

在 c + + 11 中， [nullptr](../cpp/nullptr.md)类型应首选用于 C 样式 null 指针。

### <a name="pointer-expression-conversions"></a>指针表达式转换

带数组类型的所有表达式都可以转换为同一类型的指针。 转换的结果是指向第一个数组元素的指针。 下面的示例演示了这样的转换：

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

生成返回特定类型的函数的表达式将转换为指向返回该类型的函数的指针，以下情况除外：

- 表达式用作地址运算符（ **&** ）的操作数。

- 表达式用作到 function-call 运算符的操作数。

## <a name="reference-conversions"></a>引用转换

在这些情况下，可以将对类的引用转换为对基类的引用：

- 指定的基类是可访问的。

- 转换是明确的。 （有关不明确的基类引用的详细信息，请参阅[多个基类](../cpp/multiple-base-classes.md)。）

转换的结果为指向表示基类的子对象的指针。

## <a name="pointer-to-member"></a>指向成员的指针

指向可在赋值、初始化、比较和其他语句中转换的类成员的指针。 本节描述以下指向成员的指针转换：

### <a name="pointer-to-base-class-member"></a>指向基类成员的指针

当满足以下条件时，指向基类的成员的指针可以转换为指向派生自基类的类的成员的指针：

- 从指向派生类的指针到基类指针的反向转换可以访问。

- 派生类并非以虚拟方式从基类继承。

当左操作数是指向成员的指针时，右操作数必须是 pointer-to-member 类型或计算结果为 0 的常量表达式。 此赋值仅在以下情况下有效：

- 右操作数是指向与左操作数相同的类的成员的指针。

- 左操作数是指向以公共但不明确的方式派生自右操作数的类的成员的指针。

### <a name="null-pointer-to-member-conversions"></a>指向成员转换的 null 指针

计算结果为零的整数常量表达式将转换为 null 指针。 此指针始终将与指向任意有效对象或函数的指针进行比较。 异常是指向基于对象的指针，它们可以具有相同的偏移量，并且仍指向不同的对象。

以下代码演示了指向类 `i` 中的成员 `A` 的指针的定义。 指针 `pai` 将初始化为 0，因此是 null 指针。

```cpp
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

## <a name="see-also"></a>另请参阅

[C++语言参考](../cpp/cpp-language-reference.md)