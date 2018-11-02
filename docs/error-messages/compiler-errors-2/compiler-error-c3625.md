---
title: 编译器错误 C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: 08ad1d09cb9149811566f67a585a718340254de9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635381"
---
# <a name="compiler-error-c3625"></a>编译器错误 C3625

“native_type”：本机类型不能从托管或 WinRT 类型“type”派生

本机类不能从托管或 WinRT 类继承。 有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3625：

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
