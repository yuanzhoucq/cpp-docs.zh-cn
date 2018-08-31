---
title: 编译器警告 （等级 1） C4138 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc3102f18021c16663bdf61dcde6df5e6893d46c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197083"
---
# <a name="compiler-warning-level-1-c4138"></a>编译器警告（等级 1）C4138
在注释外找到“*/”  
  
 结束注释分隔符前面没有开始注释分隔符。 编译器将假定星号之间有空格 (<strong>\*</strong>) 和正斜杠 （/）。  
  
## <a name="example"></a>示例  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 此警告可由嵌套注释引起。  
  
 如果注释掉包含注释的代码段，在 **#if / #endif** 块中包含代码，并将控制表达式设置为零，可能会解决此警告：  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```