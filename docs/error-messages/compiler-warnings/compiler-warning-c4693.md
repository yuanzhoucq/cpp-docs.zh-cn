---
title: "编译器警告 C4693 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4693
dev_langs:
- C++
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1bd881645b36e29be987850c1ceb9f3b4fd35b9d
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4693"></a>编译器警告 C4693
“class”：密封的抽象类不能具有任何实例成员“Test”  
  
 如果标记的类型[密封](../../windows/sealed-cpp-component-extensions.md)和[抽象](../../windows/abstract-cpp-component-extensions.md)，它只能具有静态成员。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4693。  
  
```  
// C4693.cpp  
// compile with: /clr /c  
public ref class Public_Ref_Class sealed abstract {  
public:  
   void Test() {}   // C4693  
   static void Test2() {}   // OK  
};  
```
