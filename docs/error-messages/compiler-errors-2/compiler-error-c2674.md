---
title: "编译器错误 C2674 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2674
dev_langs: C++
helpviewer_keywords: C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e95a91ac0610661d739ff7f2a4964ac45725b74e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2674"></a>编译器错误 C2674
此上下文中不允许泛型声明  
  
 未正确声明泛型。 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2674。  
  
```  
// C2674.cpp  
// compile with: /clr /c  
void F(generic <class T> ref class R1);   // C2674  
generic <class T> ref class R2 {};   // OK  
```