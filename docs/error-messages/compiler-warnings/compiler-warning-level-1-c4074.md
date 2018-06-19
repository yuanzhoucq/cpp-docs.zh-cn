---
title: 编译器警告 （等级 1） C4074 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4074
dev_langs:
- C++
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9072728660ca78097a1e36e492670a614bb2b2f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274698"
---
# <a name="compiler-warning-level-1-c4074"></a>编译器警告 （等级 1） C4074
初始值设定项放置在编译器保留初始化区域  
  
 编译器初始化区域中，通过指定[#pragma init_seg](../../preprocessor/init-seg.md)，Microsoft 保留。 可能的 C 运行库在初始化之前执行此区域中的代码。  
  
 下面的示例生成 C4074:  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```