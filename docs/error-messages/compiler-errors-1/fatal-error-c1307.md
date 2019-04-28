---
title: 错误 C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338527"
---
# <a name="fatal-error-c1307"></a>错误 C1307

自收集配置文件数据后已编辑了程序

使用时[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 链接器检测到 /ltcg: pginstrument 后已重新编译输入的模块和模块已更改为其中现有配置文件数据已不再相关的点。 例如，如果在重新编译模块中更改的调用关系图，编译器将生成 C1307。

若要解决此错误，请运行 /ltcg: pginstrument、 重做所有测试运行，并运行 /ltcg: pgoptimize。 如果您不能运行 /ltcg: pginstrument 和重做所有测试运行，使用 /LTCG:PGUPDATE 而不是 /ltcg: pgoptimize 创建优化的映像。