---
title: 编译器警告 （等级 1） C4612 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0983f5d0bb89eaf1daee94468b318557bc83cd05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281877"
---
# <a name="compiler-warning-level-1-c4612"></a>编译器警告（等级 1）C4612
包含文件名中有错误  
  
 当文件名不正确或缺失时，此警告与 **#pragma include_alias** 一起出现。  
  
 自变量 **#pragma include_alias**语句可以使用引号 (**"***filename***"**) 或尖括号形式 ( **\< ***filename***>**)，但两者必须使用相同的形式。  
  
## <a name="example"></a>示例  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```