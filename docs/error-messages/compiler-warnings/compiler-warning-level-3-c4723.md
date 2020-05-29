---
title: 编译器警告（等级 3）C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: 3a47c6f7e83abfc785d602d8ee0734be5d0fa962
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174084"
---
# <a name="compiler-warning-level-3-c4723"></a>编译器警告（等级 3）C4723

潜在的被0除

除法运算中的第二个操作数在编译时计算为零，并提供未定义的结果。

仅当使用[/og](../../build/reference/og-global-optimizations.md)或表示/Og. 的优化选项时，才发出此警告。

编译器可能生成了零操作数。
