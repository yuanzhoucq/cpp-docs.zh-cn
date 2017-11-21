---
title: "编译器错误 C3490 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3490
dev_langs: C++
helpviewer_keywords: C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42923edc2d238e7f0b64858561f7d23d211abd80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3490"></a>编译器错误 C3490
无法修改 var，因为正在通过 const 对象对其进行访问  
  
 在 `const` 方法中声明的 lambda 表达式不能修改不可变成员数据。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从方法声明删除 `const` 修饰符。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3490，因为它修改 `_i` 方法中的成员变量 `const` ：  
  
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