---
title: 编译器警告 （等级 1） C4939 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 459674bb4e6899563a18943f7ba510a6168d0e28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296879"
---
# <a name="compiler-warning-level-1-c4939"></a>编译器警告（等级 1）C4939
\#杂注 vtordisp 已弃用，将 Visual c + + 的未来版本中删除  
  
 将从 Visual C++ 将来的版本中删除 [vtordisp](../../preprocessor/vtordisp.md) 杂注。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4939。  
  
```  
// C4939.cpp  
// compile with: /c /W1  
#pragma vtordisp(off)   // C4939  
```