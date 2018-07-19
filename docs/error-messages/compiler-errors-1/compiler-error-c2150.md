---
title: 编译器错误 C2150 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc7a84ff666fdc17f0abeec690a548f216ce975
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170143"
---
# <a name="compiler-error-c2150"></a>编译器错误 C2150
  
> *标识符*： 位域必须具有类型 int、 signed 的 int 或 unsigned 的 int  
  
 位域的基类型必须是`int`， `signed int`，或`unsigned int`。  
  
## <a name="example"></a>示例  
  
 此示例演示如何可能会遇到 C2150，以及如何修复此错误：  
  
```cpp  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;      // OK  
};  
```