---
title: "编译器错误 C3737 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3737
dev_langs:
- C++
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: af179d622ffe8354352cc6b87ab009b825e55b36
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3737"></a>编译器错误 C3737
delegate： 委托可能没有显式调用约定  
  
 不能指定[调用约定](../../cpp/calling-conventions.md)为`delegate`。  
  
## <a name="example"></a>示例  
下面的示例生成 C3737:  
  
```  
// C3737a.cpp  
// compile with: /clr  
delegate void __stdcall MyFunc();   // C3737  
// Try the following line instead.  
// delegate void MyFunc();  
  
int main() {  
}  
```  

