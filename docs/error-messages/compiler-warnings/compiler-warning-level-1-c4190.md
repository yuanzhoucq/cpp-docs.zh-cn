---
title: "编译器警告 （等级 1） C4190 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf45c0737f52da93f93c1f95d313771f0e92a10e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告 （等级 1） C4190
identifier1 具有 C 链接指定，但它返回 UDT 与 C 不兼容的 identifier2  
  
 函数指针作为返回类型具有 UDT （用户定义类型，这是类、 结构、 枚举或联合） 和`extern`"C"链接。 这是合法的如果︰  
  
-   从 c + + 发生对此函数的所有调用。  
  
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
