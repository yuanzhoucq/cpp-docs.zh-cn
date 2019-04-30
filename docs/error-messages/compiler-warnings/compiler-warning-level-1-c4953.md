---
title: 编译器警告（等级 1）C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384148"
---
# <a name="compiler-warning-level-1-c4953"></a>编译器警告（等级 1）C4953

> 被内联方*函数*已编辑过收集配置文件数据后，不使用配置文件数据

当使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到在 `/LTCG:PGINSTRUMENT` 之后重新编译的一个输入模块，该模块具有编辑过的函数 (*function*)，在该模块内，现有测试运行将该函数标识为内联的候选项。 但是，重新编译该模块后，此函数不再是内联的候选项。

此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。