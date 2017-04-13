---
title: "编译器错误 C3488 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 6c7f36a63d5922672e89faf0c7d73c95100b256d
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3488"></a>编译器错误 C3488
当默认捕获模式为按引用捕获时，不允许使用“var”  
  
 当指定 lambda 表达式的默认捕获模式为按引用捕获时，无法按引用将变量传递给该表达式的捕获子句。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   不要显式将变量传递给捕获子句，或者  
  
-   不要将按引用指定为默认捕获模式，或者  
  
-   将按值指定为默认捕获模式，或者  
  
-   按值将变量传递到捕获子句。 （这可能会更改 lambda 表达式的行为。）  
  
## <a name="example"></a>示例  
 下面的示例生成 C3488，因为对变量 `n` 的引用出现在默认模式为按引用的 lambda 表达式的捕获子句中：  
  
```  
// C3488a.cpp  
  
int main()  
{  
   int n = 5;  
   [&, &n]() { return n; } (); // C3488  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示 C3488 的四种可能的解决方法：  
  
```  
// C3488b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass &n to the capture clause.  
   [&]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-reference as the default capture mode.  
   [&n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-value as the default capture mode.  
   [=, &n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by value to the capture clause.  
   [n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
