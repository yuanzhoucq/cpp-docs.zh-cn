---
title: 编译器错误 C3386 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3386
dev_langs:
- C++
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d378c92fbeff4e8738450e2e49c42c00bd46a6c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258070"
---
# <a name="compiler-error-c3386"></a>编译器错误 C3386
type: __declspec （dllexport) /\__declspec(dllimport) 不能应用于托管或 WinRTtype  
  
 `dllimport`和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修饰符都不是有效的托管或 Windows 运行时类型。  
  
 下面的示例生成 C3386，并演示如何修复此错误：  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```