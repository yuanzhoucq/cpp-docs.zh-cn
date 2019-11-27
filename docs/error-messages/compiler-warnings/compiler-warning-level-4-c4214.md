---
title: 编译器警告（等级 4）C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 85f37810708eff43574129f42dd8444fe7dc37c2
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541906"
---
# <a name="compiler-warning-level-4-c4214"></a>编译器警告（等级 4）C4214

使用了非标准扩展： int 以外的位域类型

对于默认的 Microsoft 扩展（/Ze），位域结构成员可以是任何整数类型。

## <a name="example"></a>示例

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

此类位域在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。