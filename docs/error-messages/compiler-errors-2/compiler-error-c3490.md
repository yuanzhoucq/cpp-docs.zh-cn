---
title: "编译器错误 C3490 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: 7
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 83a215b1c4883ba7ed4b285af8c4efafe2cfaa05
ms.lasthandoff: 04/04/2017

---
# <a name="compiler-error-c3490"></a>编译器错误 C3490
无法修改 var，因为正在通过 const 对象对其进行访问  
  
 在 `const` 方法中声明的 lambda 表达式不能修改不可变成员数据。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从方法声明删除 `const` 修饰符。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3490，因为它修改成员变量`_i`中`const`方法︰  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例通过从方法声明删除 `const` 修饰符解决了错误 C3490：  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
