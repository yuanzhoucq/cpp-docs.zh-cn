---
title: 编译器错误 C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 7c59932a79534a365a20fcad25583f7addc0d624
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609596"
---
# <a name="compiler-error-c3292"></a>编译器错误 C3292

cli 命名空间不能重新打开

cli 命名空间不能在代码中声明。  有关详细信息，请参阅[Platform、 default 和 cli 命名空间](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3292。

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```