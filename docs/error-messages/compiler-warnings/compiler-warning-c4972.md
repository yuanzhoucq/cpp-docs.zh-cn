---
title: "编译器警告 C4972 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4972
dev_langs: C++
helpviewer_keywords: C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a0ac41ed06c30600c4189dbcca3af4da3dfa595f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4972"></a>编译器警告 C4972
直接修改取消装箱操作的结果或将其视为左值是不可验证的  
  
 取消引用值类型的句柄（也称为取消装箱），然后为其赋值，是不可验证的。  
  
 有关详细信息，请参阅[装箱](../../windows/boxing-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4972。  
  
```  
// C4972.cpp  
// compile with: /clr:safe  
using namespace System;  
ref struct R {  
   int ^ p;   // a value type  
};  
  
int main() {  
   R ^ r = gcnew R;  
   *(r->p) = 10;   // C4972  
  
   // OK  
   r->p = 10;  
   Console::WriteLine( r->p );  
   Console::WriteLine( *(r->p) );  
}  
```