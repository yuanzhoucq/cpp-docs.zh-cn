---
title: 编译器错误 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: a9183e1f62e7ebaf5db04a35a45806ec02169e69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637471"
---
# <a name="compiler-error-c3386"></a>编译器错误 C3386

type: __declspec （dllexport) /\__declspec(dllimport) 不能应用于托管或 WinRTtype

`dllimport`并[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修饰符都不是有效的托管或 Windows 运行时类型。

下面的示例生成 C3386，并演示如何修复此错误：

```
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```