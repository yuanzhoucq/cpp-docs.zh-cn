---
title: "具有函数声明的存储类说明符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f7d8b6ba1c0287492195ee891b1a573bf74de6cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class-specifiers-with-function-declarations"></a>具有函数声明的存储类说明符
在函数声明中，可以使用 static 或 `extern` 存储类说明符。 函数始终具有全局生存期。  
  
 **Microsoft 专用**  
  
 内部级别的函数声明的含义与外部级别的函数声明的含义相同。 这意味着，在翻译单元的剩余部分中，该函数从其声明点可见，即使它是在局部范围内声明的。  
  
 **结束 Microsoft 专用**  
  
 函数的可见性规则与变量的规则略有不同，如下所示：  
  
-   声明为 static 的函数仅在定义它的源文件中可见。 同一源文件中的函数可以调用 static 函数，但其他源文件中的函数不能通过名称直接访问它。 可以在其他源文件中使用相同的名称声明另一个 static 函数，而不会发生冲突。  
  
-   声明为 `extern` 的函数在程序中的所有源文件中都可见（除非稍后将此类函数重新声明为 static）。 任何函数均可调用 `extern` 函数。  
  
-   默认情况下，省略存储类说明符的函数声明为 `extern`。  
  
 **Microsoft 专用**  
  
 Microsoft 允许将 `extern` 标识符重新定义为 static。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [C 存储类](../c-language/c-storage-classes.md)