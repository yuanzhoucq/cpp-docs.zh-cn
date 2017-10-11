---
title: "编译器错误 C3898 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3898
dev_langs:
- C++
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c5ff2b3079de90efbf370082be4fee03dbfaab3e
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3898"></a>编译器错误 C3898
var： 类型数据成员可以只是托管类型的成员  
  
 [Initonly](../../dotnet/initonly-cpp-cli.md)本机类中声明数据成员。  `initonly`仅可将数据成员声明中的 CLR 类。  
  
 下面的示例生成 C3898:  
  
```  
// C3898.cpp  
// compile with: /clr  
struct Y1 {  
   initonly  
   static int data_var = 9;   // C3898  
};  
```  
  
 可能的解决方法：  
  
```  
// C3898b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int data_var = 9;  
};  
```
