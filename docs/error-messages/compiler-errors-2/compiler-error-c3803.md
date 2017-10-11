---
title: "编译器错误 C3803 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3803
dev_langs:
- C++
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: aec9e416833894bcd4c4d430b293e0867f544757
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3803"></a>C3803
property： 属性具有与一个其访问器 accessor 不兼容的类型  
  
 与定义的属性的类型[属性](../../cpp/property-cpp.md)与其中一个其访问器函数的返回类型不匹配。  
  
 下面的示例生成 C3803:  
  
```  
// C3803.cpp  
struct A  
{  
   __declspec(property(get=GetIt)) int i;  
   char GetIt()  
   {  
      return 0;  
   }  
  
   /*  
   // try the following definition instead  
   int GetIt()  
   {  
      return 0;  
   }  
   */  
}; // C3803  
  
int main()  
{  
}  
```
