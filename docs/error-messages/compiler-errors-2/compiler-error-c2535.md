---
title: "编译器错误 C2535 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0af3ce8f0f3fe89d8e2f120f1b9b16383f11ef6a
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2535"></a>编译器错误 C2535
identifier： 已定义或声明的成员函数  
  
 无法通过使用多个定义或重载函数的声明中的同一形式参数列表导致此错误。  
  
 如果您因为 Dispose 函数获得 C2535，请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)有关详细信息。  
  
 如果您正在编译的 ATL 项目，请参阅知识库文章 Q241852。  
  
 下面的示例生成 C2535:  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```
