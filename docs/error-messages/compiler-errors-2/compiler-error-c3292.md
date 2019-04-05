---
title: 编译器错误 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: a68d3e922532480063fe4c294e40f453885743e8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780647"
---
# <a name="compiler-error-c3292"></a>编译器错误 C3292

cli 命名空间不能重新打开

cli 命名空间不能在代码中声明。  有关详细信息，请参阅[Platform、 default 和 cli 命名空间](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3292。

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```