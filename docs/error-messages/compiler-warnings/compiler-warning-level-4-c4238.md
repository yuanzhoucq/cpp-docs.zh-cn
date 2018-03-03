---
title: "编译器警告 （等级 4） C4238 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e8e52868d97d31243f92307e9bfd158c818c2f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4238"></a>编译器警告（等级 4）C4238
使用的非标准扩展： 类右值用作左值  
  
 与以前版本的 Visual c + +，Microsoft 扩展的兼容性 (**/Ze**) 允许你使用的类类型，如在上下文中的为右值的隐式或显式采用其地址。 在某些情况下，如以下示例中，这可能是危险。  
  
## <a name="example"></a>示例  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 这种用法会导致在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。