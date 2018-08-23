---
title: main 函数限制 |Microsoft Docs
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
ms.openlocfilehash: 981d4c8c0ef30993811e5dbb6fd0a112a6447011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406489"
---
# <a name="main-function-restrictions"></a>main 函数限制
几个限制适用于**主要**并不适用于任何其他 C++ 函数的函数。 **主要**函数：  
  
-   不能重载 (请参阅[函数重载](function-overloading.md))。  
  
-   不能声明为**内联**。  
  
-   不能声明为**静态**。  
  
-   不能提取其地址。  
  
-   无法被调用。  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)