---
title: "编译器警告 （等级 1） C4965 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4965
dev_langs: C++
helpviewer_keywords: C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f92cc2115bc35c669b4d45784e1e1d79875551e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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