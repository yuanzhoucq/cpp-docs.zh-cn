---
title: 编译器警告 (等级 1) C4731 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31bdf972ef3791760469251dc4d0bf19627bded2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4731"></a>编译器警告（等级 1）C4731
指针： 帧指针寄存器注册修改通过内联程序集代码  
  
 已修改帧指针寄存器。 你必须保存和还原的寄存器在内联程序集块或框架变量 （本地或参数，具体取决于修改的寄存器），或你的代码可能无法正常工作。  
  
 下面的示例生成 C4731:  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP 为帧指针 （不允许 FPO），并且对其进行修改。 当`p`晚引用，它引用相对于`EBP`。 但`EBP`已被覆盖的代码，所以程序将无法正常工作，甚至可能出现故障。