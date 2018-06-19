---
title: 编译器警告 （等级 1） C4965 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b731393471097fd3ba02979a48cd59513eaea9fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291897"
---
# <a name="compiler-warning-level-1-c4965"></a>编译器警告（等级 1）C4965
隐式框中的整数 0;使用 nullptr 或显式强制转换  
  
 Visual c + + 功能值类型的隐式的装箱。 导致现在使用的 c + + 托管扩展 null 赋值的指令将成为赋值为装箱的整数。  
  
 有关详细信息，请参阅[装箱](../../windows/boxing-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4965。  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```