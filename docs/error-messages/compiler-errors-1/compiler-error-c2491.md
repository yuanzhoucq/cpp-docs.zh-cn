---
title: 编译器错误 C2491 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2491
dev_langs:
- C++
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e46d63f6602af7fe962f8b139c93a4b9a561783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198880"
---
# <a name="compiler-error-c2491"></a>编译器错误 C2491
identifier： 不允许的 dllimport 函数定义  
  
 可以将数据、静态数据成员和函数声明为 `dllimport`，但不能定义为 `dllimport`。  
  
 若要解决此问题，请从函数定义中 `__declspec(dllimport)` 删除说明符。  
  
 以下示例生成 C2491：  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```