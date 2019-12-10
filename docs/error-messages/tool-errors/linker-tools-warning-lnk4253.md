---
title: 链接器工具警告 LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988084"
---
# <a name="linker-tools-warning-lnk4253"></a>链接器工具警告 LNK4253

部分 "section1" 未合并到 "section2";已合并到 "section3"

链接器检测到多个冲突的合并请求。 链接器将忽略其中一个请求。

遇到了 **/merge**选项或指令，并且由于上一个 **/merge**选项或指令（或由于链接器的隐式合并），`from` 节已合并到另一个部分。

若要解析 LNK4253，请删除其中一个合并请求。

当以视觉对象C++面向 x86 计算机和 Windows CE 目标（ARM、MIPS、SH4 和 Thumb）时，。CRT 部分现在为只读。 如果代码依赖于以前的行为（。CRT 部分是读/写的，你可能会看到意外的行为。

有关详细信息，请参阅

- [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)

- [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>示例

在下面的示例中，将指示链接器两次合并 `.rdata` 节，而不是不同的部分。 下面的示例生成 LNK4253。

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
