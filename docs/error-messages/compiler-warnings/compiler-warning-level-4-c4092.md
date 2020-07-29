---
title: 编译器警告（等级4） C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: 675e6ccbc516734a405620aa74eaa04ff2f75087
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219984"
---
# <a name="compiler-warning-level-4-c4092"></a>编译器警告（等级4） C4092

> sizeof 返回 "无符号长"

运算符的操作数 **`sizeof`** 非常大，因此 **`sizeof`** 返回了 **`unsigned long`** 。 此警告出现在 Microsoft 扩展（ [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) ）下。 在 ANSI 兼容性（ **`/Za`** ）下，将改为截断结果。
