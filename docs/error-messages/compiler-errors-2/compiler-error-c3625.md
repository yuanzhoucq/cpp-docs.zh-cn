---
title: 编译器错误 C3625 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3625
dev_langs:
- C++
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ebb7a94e807dbd8bbb9e5614f15d03e9b577858
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022582"
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
