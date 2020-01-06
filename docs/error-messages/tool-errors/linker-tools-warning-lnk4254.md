---
title: 链接器工具警告 LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988061"
---
# <a name="linker-tools-warning-lnk4254"></a>链接器工具警告 LNK4254

部分 "section1" （偏移量）已合并到具有不同特性的 "section2" （偏移量）

一个部分的内容已合并到另一个部分，但两部分的属性不同。 程序可能会产生意外的结果。 例如，你想要只读的数据现在可能在可写部分中。

若要解析 LNK4254，请修改或删除合并请求。

当以视觉对象C++面向 x86 计算机和 Windows CE 目标（ARM、MIPS、SH4 和 Thumb）时，。CRT 节是只读的。 如果代码依赖于以前的行为（。CRT 部分是读/写的，你可能会看到意外的行为。

有关详细信息，请参阅

- [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)

- [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>示例

下面的示例生成 LNK4254。

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
