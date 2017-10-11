---
title: "对于异常处理程序的限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1806c737b9adfcefbe6417fda92ddc054094d4db
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="restrictions-on-exception-handlers"></a>对于异常处理程序的限制
在代码中使用异常处理程序的主要限制是不能使用 `goto` 语句跳转到 `__try` 语句块。 相反，您必须通过常规控制流进入此语句块。 您可随意跳出 `__try` 语句块和嵌套异常处理程序。  
  
## <a name="see-also"></a>另请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
