---
title: 编译器错误 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: ca78433fcb835ad60b553be28ea746f0f880b315
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743245"
---
# <a name="compiler-error-c3386"></a>编译器错误 C3386

"type"：不能将 __declspec （dllexport）/\__declspec （dllimport）应用于托管或 WinRTtype

`dllimport` 和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修饰符在托管或 Windows 运行时类型上无效。

下面的示例生成 C3386，并演示如何修复此错误：

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
