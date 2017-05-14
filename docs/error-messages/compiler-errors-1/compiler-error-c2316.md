---
title: "编译器错误 C2316 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 60e5fb2346c92b3005e7cbfe1663d43cc0a12cdc
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2316"></a>编译器错误 C2316

> *异常*︰ 无法作为析构函数和/或复制构造函数都不可访问捕获  
  
通过值或引用捕获了异常，但复制构造函数和/或赋值运算符无法访问。  
  
通过在 Visual Studio 2003 中之前, 的 Visual c + + 版本接受此代码，但现在会导致错误。  
  
进行此错误适用于错误的 catch 语句的 MFC 异常派生自 Visual Studio 2015 中的一致性更改`CException`。 因为`CException`有一个继承私有复制构造函数，类和及其派生非可复制，无法传递的值，这还意味着无法通过值捕获它们。 捕获导致未捕获的异常，在运行时，以前的值由捕获 MFC 异常的语句，但现在编译器正确地标识此情形以及报表错误 C2316。 若要解决此问题，我们建议你使用 MFC TRY/CATCH 宏，而不是编写您自己的异常处理程序但不适合你的代码，如果捕获 MFC 异常由引用相反。   
  
## <a name="example"></a>示例  
 下面的示例生成 C2316：  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```
