---
title: 编译器错误 C2732 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2faf21eb6f0c73d02ea32c7d4ed53f86eec3de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233026"
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