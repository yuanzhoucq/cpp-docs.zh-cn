---
title: 链接器工具警告 LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: d2fd7238a3f57b11b91813bd40b66cb3e9f47202
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628821"
---
# <a name="linker-tools-warning-lnk4253"></a>链接器工具警告 LNK4253

部分"资料节 1"不合并到 section2';已合并到 section3

链接器检测到多个相互冲突的合并请求。 链接器将忽略其中一个请求。

一个 **/合并**遇到选项或指令与`from`节已合并到由于以前的其他部分 **/合并**选项或指令 （或由于隐式合并从链接器）。

若要解决 LNK4253，删除其中一个合并请求。

面向 x86 时计算机和使用 Visual c + +，Windows CE 目标 （ARM、 MIPS、 SH4 和滚动块）。CRT 部分现在为只读。 如果你的代码依赖于以前的行为 (。CRT 部分是读/写），您可能会看到意外的行为。

有关详细信息，请参阅

- [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)

- [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>示例

在下面的示例中，链接器将指示合并`.rdata`部分两次，但到不同的节。 下面的示例生成 LNK4253。

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```