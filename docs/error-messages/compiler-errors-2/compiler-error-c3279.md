---
title: "编译器错误 C3279 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 16bb13d226b6d4d5d5846f8302070bf0c9579cfb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3279"></a>编译器错误 C3279
不允许对在 cli 命名空间中声明的类模板进行部分专用化、显式专用化和显式实例化  
  
 `cli` 命名空间由 Microsoft 定义并包含伪模板。 Visual C++ 编译器不允许对此命名空间中的类模板进行用户定义专用化、部分专用化、显式专用化和显式实例化。  
  
 以下示例生成 C3279：  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```
