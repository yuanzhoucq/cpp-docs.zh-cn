---
title: switch 语句 (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160809"
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

*表达式*必须是整型类型，或者是对整型具有明确转换的类类型。 整数提升的执行方式如[标准转换](standard-conversions.md)中所述。

**Switch**语句体包含一系列的**case**标签和一个可选的**默认**标签。 **Case**语句中的两个常量表达式的计算结果不能为相同的值。 **默认**标签只能出现一次。 标记语句不是语法要求，但没有它们， **switch**语句毫无意义。   默认语句无需显示在末尾；它可以显示在 switch 语句体的任何位置。 case 或 default 标签只能显示在 switch 语句内。

每个**case**标签中的*常量表达式*都转换为*表达式*的类型，并与*表达式*进行比较以确定相等性。 Control 传递到**case** *常量表达式*与*expression*的值匹配的语句。 下表中显示了生成的行为。

### <a name="switch-statement-behavior"></a>switch 语句行为

|条件|操作|
|---------------|------------|
|转换后的值与提升的控制表达式的值匹配。|控制将转移到跟在该标签后面的语句。|
|没有常量与**case**标签中的常量匹配;存在**默认**标签。|控件将被传输到**默认**标签。|
|没有常量与**case**标签中的常量匹配;**默认**标签不存在。|在**switch**语句后将控制转移到语句。|

如果找到匹配的表达式，则不会妨碍按后续**case**或**默认**标签进行控制。 [Break](../cpp/break-statement-cpp.md)语句用于停止执行并将控制转移到**switch**语句之后的语句。 如果没有**break**语句，则将执行从匹配的**case**标签到**开关**末尾的每个语句（包括**默认值**）。 例如：

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

在上面的示例中，如果 `capa` 是大写 `c`，则 `A` 将递增。 `capa++` 终止**switch**语句体的执行，并将控制权传递给**while**循环后的**break**语句。 如果没有**break**语句，执行将 "贯穿" 到下一个标记语句，以便 `lettera` 和 `nota` 也将递增。 `case 'a'`的**break**语句提供了类似的目的。 如果 `c` 是小写 `a`，则 `lettera` 递增， **break**语句将终止**switch**语句体。 如果 `c` 不是 `a` 或 `A`，则将执行**默认**语句。

**Visual Studio 2017 及更高版本：** （适用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)） `[[fallthrough]]` 属性是在 c + + 17 标准中指定的。 它可用作**switch**语句中的提示，作为对编译器（或读取代码的任何人）的提示。 Microsoft C++ 编译器当前不会警告 fallthrough 行为，因此，此属性对编译器行为没有影响。 请注意，该属性应用于标记语句中的一个空语句；换而言之，分号是必需的。

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

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： switch 语句可能会引入和初始化一个变量，该变量的作用域限制为 switch 语句的块：

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

**Switch**语句的内部块可以包含具有初始化的定义，只要这些定义可访问，即不会被所有可能的执行路径跳过。 使用这些声明引入的名称具有局部范围。 例如：

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

**Switch**语句可以嵌套。 在这种情况下， **case**或**default**标签与包含它们的最近的**switch**语句相关联。

**Microsoft 专用**

Microsoft C 未限制**switch**语句中的 case 值数。 该数量仅受可用内存的限制。 ANSI C 要求在**switch**语句中至少允许使用257的 case 标签。

Microsoft C 的默认设置是启用 Microsoft 扩展。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)编译器选项禁用这些扩展。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
