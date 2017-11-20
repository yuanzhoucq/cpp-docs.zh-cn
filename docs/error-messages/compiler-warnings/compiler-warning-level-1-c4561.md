---
title: "编译器警告 （等级 1） C4561 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4561
dev_langs: C++
helpviewer_keywords: C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3706257138c1825e4075c7b131ae272df811626
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4561"></a>编译器警告（等级 1）C4561
__fastcall 与不兼容 / clr 选项： 将转换为\__stdcall  
  
 [__Fastcall](../../cpp/fastcall.md)函数调用约定不能与使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)编译器选项。 编译器将忽略对的调用`__fastcall`。 若要解决此警告，或者移除对的调用**__fastcall**或编译时不**/clr**。  
  
 下面的示例生成 C4561:  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```