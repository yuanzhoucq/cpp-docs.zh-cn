---
title: 编译器警告 （等级 1 和等级 4） C4949 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dbf80f85db7334d4bcb46402851cac601d258f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>编译器警告（等级 1 和等级 4）C4949
托管和非托管杂注为仅在使用编译时，才有意义 / clr [: 选项]  
  
 编译器将忽略[托管](../../preprocessor/managed-unmanaged.md)和非托管杂注，如果不使用编译的源代码[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 此警告为信息性。  
  
 下面的示例生成 C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 当 **#pragma 非托管**使用不带 **/clr**，C4949 是 4 级警告。  
  
 下面的示例生成 C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```