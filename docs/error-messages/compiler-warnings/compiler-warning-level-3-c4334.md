---
title: 编译器警告 （等级 3） C4334 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f26749c968c3cac18b509046633ba3d91d15a4be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4334"></a>编译器警告（等级 3）C4334
operator： 结果的 32 位 shift 隐式转换为 64 位 （是否 64 位位移？）  
  
 32 位位移的结果已隐式转换为 64 位和 64 位 shift 本来编译器怀疑。  若要解决此警告，请使用 64 位 shift 或显式将 shift 结果转换为 64 位。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4334。  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```