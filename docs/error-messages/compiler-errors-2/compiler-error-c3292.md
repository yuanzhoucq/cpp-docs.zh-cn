---
title: 编译器错误 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 566c92a5dc24c28b334653c6b5507b0bd9330992
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760122"
---
# <a name="compiler-error-c3292"></a>编译器错误 C3292

cli 命名空间不能重新打开

cli 命名空间不能在代码中声明。  有关详细信息，请参阅[平台默认 cli 命名空间](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3292。

```cpp
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```
