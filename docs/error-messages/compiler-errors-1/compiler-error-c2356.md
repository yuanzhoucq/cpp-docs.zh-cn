---
title: 编译器错误 C2356 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9dfb13f388c6c40c6c1853ab8e87b2e39edbc1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195199"
---
# <a name="compiler-error-c2356"></a>编译器错误 C2356
在翻译单元期间，初始化段不得更改。  
  
 可能的原因：  
  
-   `#pragma init_seg` 跟在段初始化代码  
  
-   `#pragma init_seg` 前面是另一个 `#pragma init_seg`  
  
 若要解决，将移动到的模块开头的段初始化代码。 如果必须初始化多个区域，将它们移到单独的模块。  
  
 下面的示例生成 C2356:  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```