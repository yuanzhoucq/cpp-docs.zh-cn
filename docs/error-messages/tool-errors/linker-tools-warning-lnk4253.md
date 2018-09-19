---
title: 链接器工具警告 LNK4253 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d26d688825f504cbce8224adc9a5766a555d2fc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016814"
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