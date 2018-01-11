---
title: "编译器警告 （等级 3） C4334 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4334
dev_langs: C++
helpviewer_keywords: C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7218caa399aec0bd1b9755fb6d0942991732121e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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