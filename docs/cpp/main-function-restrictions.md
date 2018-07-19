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
ms.openlocfilehash: 3114f1ef379495f36f4231dbad6fd41ac145bcfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941741"
---
# <a name="main-function-restrictions"></a>main 函数限制
多个限制应用于`main`不适用于任何其他 c + + 函数的函数。 `main`函数：  
  
-   不能重载 (请参阅[函数重载](function-overloading.md))。  
  
-   不能声明为**内联**。  
  
-   不能声明为**静态**。  
  
-   不能提取其地址。  
  
-   无法被调用。  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)