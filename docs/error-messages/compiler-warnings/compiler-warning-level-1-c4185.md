---
title: 编译器警告 （等级 1） C4185 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4185
dev_langs:
- C++
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf07335b8a3e5715adb954f2a544791b5d2b1d80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276856"
---
# <a name="compiler-warning-level-1-c4185"></a>编译器警告（等级 1）C4185
忽略未知的 #import 特性“attribute”  
  
 该特性不是有效的 `#import`特性。 它将被忽略。  
  
## <a name="example"></a>示例  
  
```  
// C4185.cpp  
// compile with: /W1 /c  
#import "stdole2.tlb" no_such_attribute   // C4185  
```