---
title: 编译器错误 C2739 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2739
dev_langs:
- C++
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1448c47ee5f4bdb94cc99e3636b3fcf498ba9f6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231844"
---
# <a name="compiler-error-c2739"></a>编译器错误 C2739
“number”: 显式托管或 WinRT 数组维度必须介于 1 和 32 之间  
  
 数组维度不在 1 和 32 之间。  
  
 下面的示例生成 C2739，并演示如何修复此错误：  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```