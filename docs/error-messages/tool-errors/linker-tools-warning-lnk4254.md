---
title: 链接器工具警告 LNK4254 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ef421cbfa87ecab8a27dfa796eaa4eaacf7b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064641"
---
# <a name="linker-tools-warning-lnk4254"></a>链接器工具警告 LNK4254

部分"资料节 1"（偏移量） 合并到 section2 （偏移量） 具有不同的属性

一个部分的内容已合并到另一个，但不同的两个部分的属性。 您的程序可能会产生意外的结果。 例如，你想要读取的数据可能现在只能在可写部分。

若要解决 LNK4254，修改或删除合并请求。

面向 x86 时计算机和使用 Visual c + +，Windows CE 目标 （ARM、 MIPS、 SH4 和滚动块）。CRT 部分是只读的。 如果你的代码依赖于以前的行为 (。CRT 部分是读/写），您可能会看到意外的行为。

有关详细信息，请参阅

- [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)

- [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>示例

下面的示例生成 LNK4254。

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```