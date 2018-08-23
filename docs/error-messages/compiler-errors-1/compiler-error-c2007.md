---
title: 编译器错误 C2007 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2007
dev_langs:
- C++
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 159a4b8f9dffc4f6ee96b0bb1935682f9f6db281
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163532"
---
# <a name="compiler-error-c2007"></a>编译器错误 C2007
\#定义语法  
  
 后未出现标识符`#define`。 若要解决此错误，使用标识符。  
  
 下面的示例生成 C2007:  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 可能的解决方法：  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```