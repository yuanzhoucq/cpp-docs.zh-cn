---
title: "编译器错误 C2341 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2341
dev_langs: C++
helpviewer_keywords: C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03ceeb7f34ca7aca58151174c327161b18f3678f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2341"></a>编译器错误 C2341
section name： 必须使用 #pragma data_seg、 code_seg 或之前的部分，用于定义段  
  
 [分配](../../cpp/allocate.md)语句是指由尚未定义段[code_seg](../../preprocessor/code-seg.md)， [data_seg](../../preprocessor/data-seg.md)，或[部分](../../preprocessor/section.md)杂注。  
  
 下面的示例生成 C2341:  
  
```  
// C2341.cpp  
// compile with: /c  
__declspec(allocate(".test"))   // C2341  
int j = 1;  
```  
  
 可能的解决方法：  
  
```  
// C2341b.cpp  
// compile with: /c  
#pragma data_seg(".test")  
__declspec(allocate(".test"))  
int j = 1;  
```