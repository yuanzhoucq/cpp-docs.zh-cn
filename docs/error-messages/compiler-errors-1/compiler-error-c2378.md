---
title: 编译器错误 C2378 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2378
dev_langs:
- C++
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01ba6f8aed7964b36ccfc665e29b393c9a593782
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196044"
---
# <a name="compiler-error-c2378"></a>编译器错误 C2378
“identifier”：重定义；符号不能使用 typedef 重载  
  
 标识符已重定义为 `typedef`。  
  
 下面的示例生成 C2378：  
  
```  
// C2378.cpp  
// compile with: /c  
int i;  
typedef int i;   // C2378  
typedef int b;   // OK  
```