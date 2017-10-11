---
title: "编译器警告 C4950 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4950
dev_langs:
- C++
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6a922a0ee324afcf5f263abe2189e4071c5575c7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4950"></a>编译器警告 C4950
“type_or_member”：标记为过时  
  
将成员或类型标记为过时与<xref:System.ObsoleteAttribute>属性。  
  
始终发出 C4950 错误。 可以通过使用来关闭此警告[警告](../../preprocessor/warning.md)杂注指令或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项。  
  
## <a name="example"></a>示例  
下面的示例生成 C4950：  
  
```cpp  
// C4950.cpp  
// compile with: /clr  
using namespace System;  
  
// Any reference to Func3 should generate an error with message  
[System::ObsoleteAttribute("Will be removed in next version", true)]  
Int32 Func3(Int32 a, Int32 b) {  
   return (a + b);  
}  
  
int main() {  
   Int32 MyInt3 = ::Func3(2, 2);   // C4950  
}  
```
