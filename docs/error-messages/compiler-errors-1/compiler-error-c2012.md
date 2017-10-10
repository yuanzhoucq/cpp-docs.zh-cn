---
title: "编译器错误 C2012 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2012
dev_langs:
- C++
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2e83597ba9224ab6cf5c70b319ff50348bd9135f
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2012"></a>编译器错误 C2012
在“<”之后缺少名称  
  
 `#include` 指令缺少必需的文件名。  
  
 以下示例生成 C2012：  
  
```  
// C2012.cpp  
#include <   // C2012 include the filename to resolve  
```  
  
 可能的解决方法：  
  
```  
// C2012b.cpp  
// compile with: /c  
#include <stdio.h>  
```
