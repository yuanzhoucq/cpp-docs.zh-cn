---
title: switch 语句 (C++)
ms.date: 11/04/2016
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 67918b7df747d3bee923da500729e60b4fe04336
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267084"
---
# <a name="switch-statement-c"></a>switch 语句 (C++)

允许根据整型表达式的值在多个代码段中进行选择。

## <a name="syntax"></a>语法

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>备注

*表达式*必须是一种整型类型或明确转换为整型类型的类类型。 如中所述执行整型提升[标准转换](standard-conversions.md)。

**切换**语句体的一系列组成**用例**标签和一个可选**默认**标签。 在任何两个常量表达式**用例**语句可以计算为相同的值。 **默认**标签可以仅出现一次。 标记的语句不是语法要求，但**切换**语句是如果没有这些无意义。   默认语句无需显示在末尾；它可以显示在 switch 语句体的任何位置。 case 或 default 标签只能显示在 switch 语句内。

*常数表达式*在每个**用例**标签转换为的类型*表达式*并与进行比较*表达式*为相等。 控制将传递给它的**用例** *常数表达式* 的值匹配 *表达式*。 下表中显示了生成的行为。

### <a name="switch-statement-behavior"></a>switch 语句行为

|条件|操作|
|---------------|------------|
|转换后的值与提升的控制表达式的值匹配。|控制将转移到跟在该标签后面的语句。|
|没有任何常量匹配中的常量**用例**标签;**默认**标签不存在。|控制权转至**默认**标签。|
|没有任何常量匹配中的常量**用例**标签;**默认**标签不存在。|控制权转交给之后的语句**切换**语句。|

如果找到匹配的表达式，则控件不会妨碍后续**用例**或**默认**标签。 [中断](../cpp/break-statement-cpp.md)语句用于停止执行并将控制转移到之后的语句**切换**语句。 无需**中断**语句中，每个语句从匹配**用例**到末尾的标签**切换**，其中包括**默认**，是执行。 例如：

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

在上面的示例中，如果 `capa` 是大写 `c`，则 `A` 将递增。 **中断**之后的语句`capa++`终止执行**切换**语句体并将控制转移到**虽然**循环。 无需**中断**语句中，执行将"贯穿"到下一步的标记语句，以便`lettera`和`nota`也将递增。 由提供相似的用途**中断**语句`case 'a'`。 如果`c`是一个小写`a`，`lettera`会递增并**中断**语句将终止**切换**语句体。 如果`c`不是`a`或`A`，则**默认**执行语句。

**2017 及更高版本的 visual Studio:** (适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` C++ 17 标准中指定属性。 可在**切换**语句的贯穿行为旨在作为提示编译器 （或任何读取代码）。 视觉对象C++编译器当前不会警告 fallthrough 行为，因此，此属性必须对编译器行为没有影响。 请注意，该属性应用于标记的语句; 中的空语句换而言之，分号是必需的。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):Switch 语句可能会引入并初始化一个变量，其作用域被限制在 switch 语句的块：

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

内部块**切换**语句可以包含带有初始化的定义，只要它们是可访问 — 即，不会绕过的所有可能的执行路径。 使用这些声明引入的名称具有局部范围。 例如：

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

一个**切换**语句可以嵌套。 在这种情况下，**用例**或**默认**标签相关联的最近**切换**封装它们的语句。

**Microsoft 专用**

Microsoft C 未限制中的 case 值的数量**切换**语句。 该数量仅受可用内存的限制。 ANSI C 要求至少 257 case 标签中允许**切换**语句。

Microsoft C 的默认设置是启用 Microsoft 扩展。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)编译器选项来禁用这些扩展。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)