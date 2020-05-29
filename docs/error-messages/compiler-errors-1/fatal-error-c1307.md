---
title: 错误 C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203341"
---
# <a name="fatal-error-c1307"></a>错误 C1307

自收集配置文件数据后已编辑了程序

当使用[/ltcg： PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)时，链接器检测到在/LTCG： PGINSTRUMENT 之后重新编译的输入模块，并已将该模块更改为现有配置文件数据不再相关的点。 例如，如果调用关系图在重新编译的模块中发生了更改，则编译器将生成 C1307。

若要解决此错误，请运行/LTCG： PGINSTRUMENT，重做所有测试运行，并运行/LTCG： PGOPTIMIZE。 如果无法运行/LTCG： PGINSTRUMENT 和 redo 所有测试运行，请使用/LTCG： PGUPDATE 而不是/LTCG： PGOPTIMIZE 创建优化的映像。
