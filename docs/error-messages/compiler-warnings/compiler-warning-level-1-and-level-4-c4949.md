---
title: "编译器警告 （等级 1 和等级 4） C4949 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 241e0295b16ae350cec213bf25b93f7ad72a0808
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

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
  
 当**#pragma 非托管**使用不带**/clr**，C4949 是 4 级警告。  
  
 下面的示例生成 C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```
