---
title: 编译器错误 C2286 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2286
dev_langs:
- C++
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ddfb523252572fb985b660f1d4dbf5b1d790df1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171921"
---
# <a name="compiler-error-c2286"></a>编译器错误 C2286
指向成员的 identifier 表示已设置为继承-忽略声明  
  
 类存在两个不同的指针到成员表示形式。  
  
 有关详细信息，请参阅[继承关键字](../../cpp/inheritance-keywords.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2286：  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```