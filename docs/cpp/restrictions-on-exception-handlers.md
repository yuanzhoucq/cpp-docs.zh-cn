---
title: "对于异常处理程序的限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42207a9bc1e9a355e6785a609ab0b130be063d55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="restrictions-on-exception-handlers"></a>对于异常处理程序的限制
在代码中使用异常处理程序的主要限制是不能使用 `goto` 语句跳转到 `__try` 语句块。 相反，您必须通过常规控制流进入此语句块。 您可随意跳出 `__try` 语句块和嵌套异常处理程序。  
  
## <a name="see-also"></a>另请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)