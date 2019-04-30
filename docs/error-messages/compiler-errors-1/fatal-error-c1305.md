---
title: 错误 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397492"
---
# <a name="fatal-error-c1305"></a>错误 C1305

配置文件数据库 pgd_file 是用于不同的体系结构

另一个平台已传递给从 /ltcg: pginstrument 操作生成一个.pgd 文件[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [按配置优化](../../build/profile-guided-optimizations.md)可用于 x86 和 x64 平台。 但是，与针对一个平台 /ltcg: pginstrument 操作生成的.pgd 文件不是有效作为针对不同平台 /ltcg: pgoptimize 的输入。

若要解决此错误，仅传递使用 /ltcg: pginstrument 到 /ltcg: pgoptimize 同一平台上创建一个.pgd 文件。