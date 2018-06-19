---
title: 编译器警告 （等级 1） C4926 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527c03d4f71048064c2120f7cfa9730de198fd46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290850"
---
# <a name="compiler-warning-level-1-c4926"></a>编译器警告（等级 1）C4926
“identifier”：已定义符号：忽略特性  
  
 已找到前向声明，但已存在具有相同名称的特性化的构造。 忽略前向声明的特性。  
  
 下面的示例生成 C4926：  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```