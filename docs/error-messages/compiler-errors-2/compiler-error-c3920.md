---
title: 编译器错误 C3920 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ced0a0f8fa2b6694de4dd901d71f6721e12493b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3920"></a>编译器错误 C3920
运算符： 不能定义后缀递增/递减 WinRT 或 CLR 运算符，调用后缀 WinRT 或 CLR 运算符将调用相应的前缀 WinRT 或 CLR 运算符 (op_Increment/op_Decrement)，但具有后缀语义  
  
 Windows 运行时和 CLR 不支持后缀运算符并且不允许使用用户定义的后缀运算符。  可以定义前缀运算符并且将其用于前递增和后递增操作。  
  
 以下示例将生成 C3920，并演示如何修复此错误：  
  
```  
// C3920.cpp  
// compile with: /clr /LD  
public value struct V {  
   static V operator ++(V me, int)  
   // try the following line instead  
   // static V operator ++(V me)  
   {   // C3920  
      me.m_i++;  
      return me;  
   }  
  
   int m_i;  
};  
  
```