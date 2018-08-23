---
title: 编译器错误 C3179 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3179
dev_langs:
- C++
helpviewer_keywords:
- C3179
ms.assetid: 60d7e41b-25fd-48ac-8b79-830c062f4dcd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6234eceb35bda37a3616113d3010fe09cb669c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246025"
---
# <a name="compiler-error-c3179"></a>编译器错误 C3179
不允许未命名的托管类型或 WinRT 类型  
  
所有 CLR 与 WinRT 类和结构都必须具有名称。  
  
下面的示例生成 C3179，并演示如何修复此错误：  
  
```  
// C3179a.cpp  
// compile with: /clr /c  
typedef value struct { // C3179  
// try the following line instead  
// typedef value struct MyStruct {  
   int i;  
} V;  
```  
