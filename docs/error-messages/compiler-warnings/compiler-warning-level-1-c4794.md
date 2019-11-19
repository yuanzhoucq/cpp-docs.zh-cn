---
title: 编译器警告（等级 1）C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7d669280c0dc6a730a22480e602dac8cc6153449
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052368"
---
# <a name="compiler-warning-level-1-c4794"></a>编译器警告（等级 1）C4794

线程本地存储区变量“variable”的段由“section name”改为“.tls$”

你使用了 [#pragma data_seg](../../preprocessor/data-seg.md) 向未以 .tls$ 开始的节中放置 tls 变量。

.Tls$*x* 节将出现在定义了 [__declspec (thread)](../../cpp/thread.md) 变量的对象文件中。 EXE 或 DLL 中的 .tls 节将从这些节中产生。

## <a name="example"></a>示例

下面的示例生成 C4794：

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```