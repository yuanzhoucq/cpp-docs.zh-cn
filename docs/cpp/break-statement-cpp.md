---
title: "break 语句 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "break_cpp"
  - "break"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "break 关键字 [C++]"
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# break 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`break` 语句可终止执行最近的封闭循环或其所在条件语句。  控制权将传递给该语句结束之后的语句（如果有的话）。  
  
## 语法  
  
```  
break;  
```  
  
## 备注  
 `break` 语句与 [switch](../cpp/switch-statement-cpp.md) 条件语句以及 [do](../cpp/do-while-statement-cpp.md)、[for](../cpp/for-statement-cpp.md) 和 [while](../cpp/while-statement-cpp.md) 循环语句配合使用。  
  
 在 `switch` 语句中，`break` 语句将导致程序执行 `switch` 语句之外的下一语句。  如果没有 `break` 语句，则将执行从匹配的 `case` 标签到 `switch` 语句末尾之间的每个语句，包括 `default` 子句。  
  
 在循环中，`break` 语句将终止执行最近的 `do`、`for` 或 `while` 封闭语句。  控制权将传递给终止语句之后的语句（如果有的话）。  
  
 在嵌套语句中，`break` 语句只终止直接包围它的 `do`、`for`、`switch` 或 `while` 语句。  你可以使用 `return` 或 `goto` 语句从较深嵌套的结构转移控制权。  
  
## 示例  
 以下代码演示如何在 `for` 循环中使用 `break` 语句。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // An example of a standard for loop  
    for (int i = 1; i < 10; i++)  
    {  
        cout << i << '\n';  
        if (i == 4)  
            break;  
    }  
  
    // An example of a range-based for loop  
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};  
  
    for (int i : nums) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
    }  
}  
```  
  
  **在每个用例中：**  
**1**  
**2**  
**3** 以下代码演示如何在 `while` 循环和 `do` 循环中使用 `break`。  
  
```cpp  
  
#include <iostream>  
using namespace std;  
  
int main() {  
    int i = 0;  
  
    while (i < 10) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    }  
  
    i = 0;  
    do {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    } while (i < 10);  
}  
```  
  
  **在每个用例中：**  
**0**  
**1**  
**2**  
**3** 以下代码演示如何在 switch 语句中使用 `break`。  如果你要分别处理每个用例，则必须在每个用例中使用 `break`；如果不使用 `break`，则执行下一用例中的代码。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
enum Suit{ Diamonds, Hearts, Clubs, Spades };  
  
int main() {  
  
    Suit hand;  
    . . .  
    // Assume that some enum value is set for hand  
    // In this example, each case is handled separately  
    switch (hand)  
    {  
    case Diamonds:  
        cout << "got Diamonds \n";  
        break;  
    case Hearts:  
        cout << "got Hearts \n";  
        break;  
    case Clubs:  
        cout << "got Clubs \n";  
        break;  
    case Spades:  
        cout << "got Spades \n";  
        break;  
    default:   
          cout << "didn't get card \n";  
    }  
    // In this example, Diamonds and Hearts are handled one way, and  
    // Clubs, Spades, and the default value are handled another way  
    switch (hand)  
    {  
    case Diamonds:  
    case Hearts:  
        cout << "got a red card \n";  
        break;  
    case Clubs:  
    case Spades:   
    default:  
        cout << "didn't get a red card \n";  
    }  
}  
```  
  
## 请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [continue 语句](../cpp/continue-statement-cpp.md)