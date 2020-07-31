---
title: 编译器错误 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: 0cb6235f1b6bc868655cc6a6ba301be1308402cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221076"
---
# <a name="compiler-error-c3386"></a>编译器错误 C3386

"type"： __declspec （dllexport）/ \_ _declspec （dllimport）不能应用于托管或 WinRTtype

`dllimport`和[dllexport](../../cpp/dllexport-dllimport.md) **`__declspec`** c "* * 修饰符在托管或 Windows 运行时类型上无效。

下面的示例生成 C3386，并演示如何修复此错误：

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
