---
title: "编译器错误 C3492 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ff183b8a5171bc3849c4e8dd132dce6d75323f4e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3492"></a>编译器错误 C3492
“var”: 不能捕获匿名联合的成员  
  
 不能捕获未命名联合的成员。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   为联合提供一个名称，并将整个此联合结构传递到 lambda 表达式的捕获列表。  
  
## <a name="example"></a>示例  
 以下示例将生成 C3492，因为它捕获匿名联合的成员：  
  
```  
// C3492a.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   };  
  
   ch = 'y';  
   [&x](char ch) { x = ch; }(ch); // C3492  
}  
```  
  
## <a name="example"></a>示例  
 通过给此联合提供名称以及将整个联合结构传递给 lambda 表达式的捕获列表，下面的示例解析了 C3492：  
  
```  
// C3492b.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   } u;  
  
   u.ch = 'y';  
   [&u](char ch) { u.x = ch; }(u.ch);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
