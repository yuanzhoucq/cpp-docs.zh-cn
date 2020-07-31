---
title: 编译器错误 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 8218233bb7a92c699952f7a506f6728386af4d17
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221063"
---
# <a name="compiler-error-c3387"></a>编译器错误 C3387

"member"： __declspec （dllexport）/ \_ _declspec （dllimport）不能应用于托管或 WinRT 类型的成员

`dllimport`和[dllexport](../../cpp/dllexport-dllimport.md) **`__declspec`** 修饰符在托管或 Windows 运行时类型的成员上无效。

下面的示例将生成 C3387，并演示如何修复此错误：

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
