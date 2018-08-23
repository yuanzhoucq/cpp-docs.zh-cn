---
title: 外部级别声明的存储类说明符 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfdae4791b89ffd78661a983fdc8c1beec77edea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392112"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>外部级别声明的存储类说明符
外部变量是文件范围内的变量。 它们在任何函数的外部定义，并且可能对许多函数可用。 只能在外部级别定义函数，因此不能将其嵌套。 默认情况下，对名称相同的外部变量和函数的所有引用都是对同一对象的引用，这表示它们具有“外部链接”。 （可以使用 static 关键字进行替代。 有关 static 的更多详细信息，请参阅本节后面的信息。）  
  
 外部级别的变量声明是变量的定义（“定义声明”）或对其他位置定义的变量的引用（“引用声明”）。  
  
 （隐式或显式）初始化变量的外部变量声明是变量的定义声明。 外部级别的定义可采用多种形式：  
  
-   使用 static 存储类说明符声明的变量。 可以使用常量表达式显式初始化 static 变量，如[初始化](../c-language/initialization.md)中所述。 如果省略初始值设定项，默认情况下变量将初始化为 0。 例如，这两个语句都被视为变量 `k` 的定义。  
  
    ```  
    static int k = 16;  
    static int k;  
    ```  
  
-   在外部级别显式初始化的变量。 例如，`int j = 3;` 是变量 `j` 的定义。  
  
 在外部级别的变量声明中（即，这些函数的外部），可以使用 static 或 `extern` 存储类说明符或完全忽略存储类说明符。 无法在外部级别使用 auto 和 register storage-class-specifier 终止符。  
  
 一旦在外部级别定义变量，该变量在翻译单元的其余部分便可见。 该变量在同一源文件中的声明之前不可见。 此外，除非引用声明使其可见，否则它在程序的其他源文件中不可见，如下文所述。  
  
 与 static 相关的规则包括：  
  
-   所有块的外部声明的不带有 static 关键字的变量在整个程序中始终保留其值。 若要限制其特定翻译单元的访问，则必须使用 static 关键字。 这将为它们提供“内部链接”。 若要使其成为整个程序的全局变量，请忽略显式存储类或使用关键字 `extern`（请参阅下一个列表中的规则）。 这将为它们提供“外部链接”。 内部链接和外部链接也在[链接](../c-language/linkage.md)中进行了讨论。  
  
-   在程序中，只可在外部级别定义变量一次。 可以在不同的翻译单元中定义具有相同名称和 static 存储类说明符的另一个变量。 由于每个 static 定义只在其自己的翻译单元中可见，因此不会发生任何冲突。 这样一来，可以隐藏必须在单个翻译单元的函数之间共享但对其他翻译单元不可见的标识符名称。  
  
-   static 存储类说明符也可应用于函数。 如果声明函数 static，则其名称在用于声明它的文件的外部不可见。  
  
 有关使用 `extern` 的规则为：  
  
-   `extern` 存储类说明符声明对在其他位置定义的变量的引用。 可以使用 `extern` 声明使另一个源文件中的定义可见，或使变量在同一源文件中的定义之前可见。 一旦在外部级别声明对变量的引用，则该变量翻译单元的其余部分是可见的，直到声明的引用出现。  
  
-   若要使 `extern` 引用有效，必须定义其引用的变量一次，并且仅在外部级别定义一次。 此定义（没有 `extern` 存储类）可位于构成程序的任何翻译单元中。  
  
## <a name="example"></a>示例  
 下面的示例阐释了外部声明：  
  
```  
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
  
```  
int i = 3;  
```  
  
 定义全局变量 `i` 并使用初始值 3 对其进行初始化。 位于使用 `i` 的第一个源文件顶部的 `extern` 的“引用”声明使全局变量在其文件中的定义声明之前可见。 此外，第二个源文件中的 `i` 的引用声明使变量在该源文件中可见。 如果翻译单元中未提供变量的定义实例，则编译器假定有  
  
```  
extern int x;  
```  
  
 一个引用声明，并且定义引用  
  
```  
int x = 0;  
```  
  
 出现在程序的另一个翻译单元中。  
  
 所有三个函数（`main`、`next` 和 `other`）都执行同一任务：它们增大 `i` 并将其打印。 打印值 4、5 和 6。  
  
 如果尚未初始化变量 `i`，则会自动将其设置为 0。 在这种情况下，值 1、2 和 3 可能已打印。 有关变量初始化的信息，请参阅[初始化](../c-language/initialization.md)。  
  
## <a name="see-also"></a>请参阅  
 [C 存储类](../c-language/c-storage-classes.md)