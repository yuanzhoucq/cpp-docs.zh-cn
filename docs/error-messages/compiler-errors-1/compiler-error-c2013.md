---
title: 编译器错误 C2013 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2013
dev_langs:
- C++
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53265c27bbac02ddbccb3b2a89b77a515e752f73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163746"
---
# <a name="compiler-error-c2013"></a>编译器错误 C2013
缺少“>”  
  
 `#include` 指令缺少右尖括号。 添加右括号可解决该错误。  
  
 下面的示例生成 C2013：  
  
```  
// C2013.cpp  
#include <stdio.h    // C2013  
```  
  
 可能的解决方法：  
  
```  
// C2013b.cpp  
// compile with: /c  
#include <stdio.h>  
```