---
title: "错误 C1104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1104
dev_langs:
- C++
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7a3f7fbff36f998716bc6639ccb718b1699ccf80
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1104"></a>错误 C1104
导入 libid 时遇到错误：“message”  
  
 导入类型库时编译器检测到问题。  例如，你不能使用 libid 指定类型库，同时还指定 `no_registry`。  
  
 有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下面的示例生成 C1104：  
  
```  
// C1104.cpp  
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```
