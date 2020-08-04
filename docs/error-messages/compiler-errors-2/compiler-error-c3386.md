---
title: 编译器错误 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: efe882db447b9ebc69d02e3b10d9e484a3cfd8a8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520443"
---
# <a name="compiler-error-c3386"></a>编译器错误 C3386

> "*type-name*"： `__declspec(dllexport)` / `__declspec(dllimport)` 不能应用于托管或 WinRT 类型

[`dllimport`](../../cpp/dllexport-dllimport.md)和 [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** 修饰符在托管或 Windows 运行时类型上无效。

下面的示例生成 C3386，并演示如何修复此错误：

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
