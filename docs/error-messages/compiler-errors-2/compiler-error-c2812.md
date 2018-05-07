---
title: 编译器错误 C2812 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28d46b0f9744f192d677d7b2df27b67e734de1b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2812"></a>编译器错误 C2812
\#导入不支持使用 /clr: pure 和 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 [#import 指令](../../preprocessor/hash-import-directive-cpp.md)不支持 **/clr: pure**和 **/clr: safe**因为`#import`需要本机编译器支持库的使用。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```