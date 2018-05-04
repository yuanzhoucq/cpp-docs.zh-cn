---
title: main 函数限制 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5be2df6e152b26bcade1970b35ad33655e8e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="main-function-restrictions"></a>main 函数限制
几个限制适用于**主要**并不适用于任何其他 C++ 函数的函数。 **主要**函数：  
  
-   无法重载 (请参阅[函数重载](function-overloading.md))。  
  
-   不能声明为**内联**。  
  
-   不能声明为**静态**。  
  
-   不能提取其地址。  
  
-   无法被调用。  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)