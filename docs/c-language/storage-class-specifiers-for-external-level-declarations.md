---
title: 外部级别声明的存储类说明符
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 6c30b8a12c0bf26bc35905872fb6fa527b367ef4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229462"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>外部级别声明的存储类说明符

外部变量是文件范围内的变量。 它们在任何函数的外部定义，并且可能对许多函数可用。 只能在外部级别定义函数，因此不能将其嵌套。 默认情况下，所有对同名外部变量和函数的引用都是对同一个对象的引用，也就是说它们具有外部链接。 （可以使用 `static` 关键字来替代此行为。）

外部级别的变量声明要么是变量的定义（定义声明），要么是对其他地方定义的变量的引用（引用声明）。

（隐式或显式）初始化变量的外部变量声明是变量的定义声明。 外部级别的定义可采用多种形式：

- 使用 `static` 存储类说明符声明的变量。 可以使用常数表达式来显式初始化 `static` 变量，如[初始化](../c-language/initialization.md)中所述。 如果省略初始值设定项，默认情况下变量将初始化为 0。 例如，这两个语句都被视为变量 `k` 的定义。

    ```C
    static int k = 16;
    static int k;
    ```

- 在外部级别显式初始化的变量。 例如，`int j = 3;` 是变量 `j` 的定义。

在外部级别（即在所有函数之外）的变量声明中，可以使用 `static` 或 `extern` 存储类说明符，也可以完全省略存储类说明符。 不能在外部级别使用 `auto` 和 `register` `storage-class-specifier` 终止符。

一旦在外部级别定义变量，该变量在翻译单元的其余部分便可见。 该变量在同一源文件中的声明之前不可见。 此外，除非引用声明使其可见，否则它在程序的其他源文件中不可见，如下文所述。

与 `static` 相关的规则包括：

- 在所有块之外声明的、没有 `static` 关键字的变量在整个程序中始终保持自己的值不变。 若要限制它们对特定翻译单元的访问，必须使用 `static` 关键字。 这给了它们内部链接。 若要让它们成为整个程序的全局变量，请省略显式存储类或使用关键字 `extern`（见下一个列表中的规则）。 这给了它们外部链接。 内部链接和外部链接也在[链接](../c-language/linkage.md)中进行了讨论。

- 在程序中，只可在外部级别定义变量一次。 可以在不同的翻译单元中定义另一个具有相同名称和 `static` 存储类说明符的变量。 由于每个 `static` 定义只在它自己的翻译单元中可见，因此不会发生任何冲突。 这提供了一种实用的方法来隐藏标识符名称，这些标识符名称必须在一个翻译单元的函数之间共用，但对其他翻译单元不可见。

- `static` 存储类说明符也可以应用于函数。 如果你声明函数 `static`，那么它的名称在声明它的文件之外是不可见的。

`extern` 的使用规则为：

- `extern` 存储类说明符声明对在其他地方定义的变量的引用。 可以使用 `extern` 声明让另一个源文件中的定义可见，或让变量先于同一源文件中的定义可见。 一旦你在外部级别声明了对变量的引用，此变量就在声明的引用所在的整个翻译单元的其余部分都是可见的。

- 若要使 `extern` 引用有效，它所引用的变量必须在外部级别定义一次，且只定义一次。 此定义（不包含 `extern` 存储类）可以位于组成程序的任何翻译单元中。

## <a name="example"></a>示例

下面的示例阐释了外部声明：

```C
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

此示例中的两个源文件包含 `i` 的总共三个外部声明。 仅一个声明是“定义声明”。 该声明

```C
int i = 3;
```

定义全局变量 `i` 并使用初始值 3 对其进行初始化。 使用 `extern` 的第一个源文件顶部的 `i` 的“引用”声明让全局变量先于文件中的定义声明可见。 此外，第二个源文件中的 `i` 的引用声明使变量在该源文件中可见。 如果翻译单元中未提供变量的定义实例，则编译器假定有

```C
extern int x;
```

一个引用声明，并且定义引用

```C
int x = 0;
```

出现在程序的另一个翻译单元中。

所有三个函数（`main`、`next` 和 `other`）都执行同一任务：它们增大 `i` 并将其打印。 打印值 4、5 和 6。

如果变量 `i` 还没有被初始化，则会自动设置为 0。 在这种情况下，值 1、2 和 3 可能已打印。 有关变量初始化的信息，请参阅[初始化](../c-language/initialization.md)。

## <a name="see-also"></a>请参阅

[C 存储类](../c-language/c-storage-classes.md)
