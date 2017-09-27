---
title: "main 函数限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 10fe82b0bb7ad700164b05ba466854db7716ba76
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="main-function-restrictions"></a>main 函数限制
几个限制适用于**主要**并不适用于任何其他 c + + 函数的函数。 **主要**函数：  
  
-   无法重载 (请参阅[函数重载](function-overloading.md))。  
  
-   不能声明为**内联**。  
  
-   不能声明为**静态**。  
  
-   不能提取其地址。  
  
-   无法被调用。  
  
## <a name="see-also"></a>另请参阅  
 [main：程序启动](../cpp/main-program-startup.md)
