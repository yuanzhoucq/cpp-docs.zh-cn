---
title: "break 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- break_cpp
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1f9c9a09652eb76511c7d059cc70eae3fb99ffd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="break-statement-c"></a>break 语句 (C++)
`break` 语句可终止执行最近的封闭循环或其所在条件语句。 控制权将传递给该语句结束之后的语句（如果有的话）。  
  
## <a name="syntax"></a>语法  
  
```  
break;  
```  
  
## <a name="remarks"></a>备注  
 `break`语句用于条件[切换](../cpp/switch-statement-cpp.md)语句与[执行](../cpp/do-while-statement-cpp.md)，[为](../cpp/for-statement-cpp.md)，和[时](../cpp/while-statement-cpp.md)循环语句。  
  
 在 `switch` 语句中，`break` 语句将导致程序执行 `switch` 语句之外的下一语句。 如果没有 `break` 语句，则将执行从匹配的 `case` 标签到 `switch` 语句末尾之间的每个语句，包括 `default` 子句。  
  
 在循环中，`break` 语句将终止执行最近的 `do`、`for` 或 `while` 封闭语句。 控制权将传递给终止语句之后的语句（如果有的话）。  
  
 在嵌套语句中，`break` 语句只终止直接包围它的 `do`、`for`、`switch` 或 `while` 语句。 你可以使用 `return` 或 `goto` 语句从较深嵌套的结构转移控制权。  
  
## <a name="example"></a>示例  
 以下代码演示如何在 `break` 循环中使用 `for` 语句。  
  
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
  
```Output  
In each case:   
1  
2  
3  
```  
  
 以下代码演示如何在 `break` 循环和 `while` 循环中使用 `do`。  
  
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
  
```Output  
In each case:  
0123  
```  
  
 以下代码演示如何在 switch 语句中使用 `break`。 如果你要分别处理每个用例，则必须在每个用例中使用 `break`；如果不使用 `break`，则执行下一用例中的代码。  
  
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
  
## <a name="see-also"></a>请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [continue 语句](../cpp/continue-statement-cpp.md)