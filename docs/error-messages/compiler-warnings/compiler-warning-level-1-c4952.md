---
title: 编译器警告（等级 1）C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537574"
---
# <a name="compiler-warning-level-1-c4952"></a>编译器警告（等级 1）C4952

> '*函数*： 在程序数据库中找到的任何配置文件数据'*pgd_file*

当使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到一个在 `/LTCG:PGINSTRUMENT` 后被重新编译且具有一个新的函数 (*function*) 存在的输入模块。

此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。