---
title: 编译器警告 （等级 4） C4571 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4571
dev_langs:
- C++
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ecd2223baec2d2ff7e743442d0b44e54c8cb05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301341"
---
# <a name="compiler-warning-level-4-c4571"></a>编译器警告（等级 4）C4571
自 Visual c + + 7.1; 以来更改的信息： 之后语义不再捕获结构化的异常 (SEH)  
  
 使用编译时 C4571 为每个之后块生成 **/EHs**。  
  
 使用编译时 **/EHs**，之后块将不会捕获结构化的异常 （除以零，null 指针，例如）; 之后块仅捕获显式引发，而 c + + 异常。  有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 默认情况下，此警告处于关闭状态。  打开此警告以确保与编译时 **/EHs** catch （...） 块不想要捕获结构化的异常。  请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 您可以通过以下方式之一解决 C4571  
  
-   使用编译 **/EHa**你仍然想要你之后块来捕获结构化的异常。  
  
-   如果您不希望你使用块来捕获结构化的异常，但你仍想要使用之后块，则不要启用 C4571。  你仍可以捕获使用结构化的异常处理关键字的结构化的异常 (**__try**， **__except**，和 **__finally**)。  但请记住，编译时 **/EHs** SEH 异常时发生不引发 c + + 异常时，将仅调用析构函数。  
  
-   将替换为特定的 c + + 异常的 catch 块之后块和 （可选） 添加结构化的异常处理围绕 c + + 异常处理 (**__try**， **__except**，和 **___identifier**)。  请参阅[结构化异常处理 （C/c + +）](../../cpp/structured-exception-handling-c-cpp.md)有关详细信息。  
  
 请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4571。  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```