---
title: "编译器警告 （等级 1） C4190 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4190
dev_langs: C++
helpviewer_keywords: C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 127eb4327826412d605f2a4a008e411880998073
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告 （等级 1） C4190
identifier1 具有 C 链接指定，但它返回 UDT 与 C 不兼容的 identifier2  
  
 函数指针具有 UDT （用户定义类型，这是类、 结构、 枚举或联合） 用作返回类型和`extern`"C"链接。 这是合法如果：  
  
-   对此函数的所有调用都发生通过 c + +。  
  
-   在 c + + 函数的定义。  
  
## <a name="example"></a>示例  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```