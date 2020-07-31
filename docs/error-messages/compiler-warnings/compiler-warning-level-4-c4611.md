---
title: 编译器警告（等级 4）C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214329"
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611

"function" 和 c + + 对象析构之间的交互是不可移植的

在某些平台上，包含的函数在 **`catch`** 超出范围时可能不支持析构函数的 c + + 对象语义。

若要避免意外的行为，请避免 **`catch`** 在具有构造函数和析构函数的函数中使用。

此警告只发出一次;请参阅[杂注警告](../../preprocessor/warning.md)。
