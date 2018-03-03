---
title: "编译器错误 C2732 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeecaab0fd9faaa6a876aa57781160df6bb26502
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2732"></a>编译器错误 C2732
链接规范与“function”的早期规范冲突  
  
 该函数已经使用其他链接说明符声明。  
  
 具有不同链接说明符的包含文件可能会导致此错误。  
  
 要修复此错误，请更改 `extern` 语句，以便这些链接一致。 特别是，不要对 `extern "C"` 块中的 `#include` 指令换行。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2732：  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```