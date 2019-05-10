---
title: 编译器警告（等级 1）C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: 4701ac40d436a9f5511f2c7cec86e8183ec2f837
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406296"
---
# <a name="compiler-warning-level-1-c4810"></a>编译器警告（等级 1）C4810

杂注 pack(show) 的值 == n

当你使用时，将发出此警告**显示**的选项[pack](../../preprocessor/pack.md)杂注。 *n* 是当前的 pack 值。

例如，下面的代码演示 C4810 警告如何处理 pack 杂注：

```
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```