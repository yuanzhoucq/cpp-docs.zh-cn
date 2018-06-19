---
title: 编译器错误 C3353 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47c9d1dd8c21e56613b9da00fc2bf4f7fbeafcca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253900"
---
# <a name="compiler-error-c3353"></a>编译器错误 C3353
“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建  
  
 使用声明委托，[委托](../../windows/delegate-cpp-component-extensions.md)关键字，只能在全局范围内声明。  
  
 以下示例生成 C3353：  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```