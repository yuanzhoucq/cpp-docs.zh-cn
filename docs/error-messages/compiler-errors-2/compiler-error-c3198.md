---
title: 编译器错误 C3198 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0516e7cae12e544195d157781e6ed86923470420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3198"></a>编译器错误 C3198
使用无效的浮点杂注： fenv_access 杂注仅在精确的模式下运行  
  
 [fenv_access](../../preprocessor/fenv-access.md)杂注已在使用[/fp](../../build/reference/fp-specify-floating-point-behavior.md)以外的设置 **/fp： 精确**。  
  
 下面的示例生成 C3198:  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```