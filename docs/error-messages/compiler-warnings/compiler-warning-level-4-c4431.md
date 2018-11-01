---
title: 编译器警告（等级 4）C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 1cef70ab02148924bf6a0f29e298b34c54b28bc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624323"
---
# <a name="compiler-warning-level-4-c4431"></a>编译器警告（等级 4）C4431

缺少类型说明符 - 假定为 int。 注意: C 不再支持默认的 int

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： Visual c + + 不再非类型化的标识符为 int 默认情况下创建。 必须显式指定标识符的类型。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

## <a name="example"></a>示例

下面的示例生成 C4431。

```
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```