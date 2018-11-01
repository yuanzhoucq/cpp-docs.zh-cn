---
title: 编译器错误 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: bd783d9510b1699b33f108a4ce8d8c491028b758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541891"
---
# <a name="compiler-error-c3387"></a>编译器错误 C3387

member: __declspec （dllexport) /\__declspec(dllimport) 不能应用于成员的托管或 WinRT 类型

`dllimport`并[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修饰符都不是有效的托管成员或 Windows 运行时类型。

下面的示例将生成 C3387，并演示如何修复此错误：

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```