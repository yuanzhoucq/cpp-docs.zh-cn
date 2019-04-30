---
title: 编译器警告（等级 4）C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401119"
---
# <a name="compiler-warning-level-4-c4214"></a>编译器警告（等级 4）C4214

使用了非标准扩展： 位字段类型而不是 int

使用默认的 Microsoft 扩展 (/Ze) 中，位域结构成员可以是任何整数类型。

## <a name="example"></a>示例

```
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

此类位域是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。