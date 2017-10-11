---
title: "编译器警告 C4956 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bad7fac98e81e39457f484960ee566c16b6fe5bc
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4956"></a>编译器警告 C4956
“type”：此类型不可验证  
  
 当指定了 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 而你的代码包含不可验证的类型时，将生成此警告。  
  
 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。  
  
 下面的示例生成 C4956：  
  
```  
// C4956.cpp  
// compile with: /clr:safe  
int* p;   // C4956  
```
