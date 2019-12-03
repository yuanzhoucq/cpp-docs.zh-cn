---
title: 编译器警告（等级 4）C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 102e9bdb2804988875d8c535eb8c266bd8fb03df
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683071"
---
# <a name="compiler-warning-level-4-c4431"></a>编译器警告（等级 4）C4431

缺少类型说明符 - 假定为 int。 注意: C 不再支持默认的 int

此错误可能是由于对 Visual Studio 2005 执行的编译器一致性工作导致的，因此默认情况下C++ ，visual Studio 不再创建非类型化标识符。 必须显式指定标识符的类型。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

## <a name="example"></a>示例

下面的示例生成 C4431。

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```