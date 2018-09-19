---
title: 错误 C1307 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f398dd9885c571ea0d66171889f20d3321a3b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085857"
---
# <a name="fatal-error-c1307"></a>错误 C1307

自收集配置文件数据后已编辑了程序

使用时[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 链接器检测到 /ltcg: pginstrument 后已重新编译输入的模块和模块已更改为其中现有配置文件数据已不再相关的点。 例如，如果在重新编译模块中更改的调用关系图，编译器将生成 C1307。

若要解决此错误，请运行 /ltcg: pginstrument、 重做所有测试运行，并运行 /ltcg: pgoptimize。 如果您不能运行 /ltcg: pginstrument 和重做所有测试运行，使用 /LTCG:PGUPDATE 而不是 /ltcg: pgoptimize 创建优化的映像。