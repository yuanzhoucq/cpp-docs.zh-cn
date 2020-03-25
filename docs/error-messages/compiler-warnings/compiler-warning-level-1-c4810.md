---
title: 编译器警告（等级 1）C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: bdeb4dd28587635a391e7b776ccd88b637a7769f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174929"
---
# <a name="compiler-warning-level-1-c4810"></a>编译器警告（等级 1）C4810

杂注 pack(show) 的值 == n

当你使用时，将发出此警告**显示**的选项[pack](../../preprocessor/pack.md)杂注。 *n* 是当前的 pack 值。

例如，下面的代码演示 C4810 警告如何处理 pack 杂注：

```cpp
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```
