---
title: 错误 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822231"
---
# <a name="fatal-error-c1305"></a>错误 C1305

配置文件数据库 pgd_file 是用于不同的体系结构

另一个平台已传递给从 /ltcg: pginstrument 操作生成一个.pgd 文件[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [按配置优化](../../build/profile-guided-optimizations.md)可用于 x86 和 x64 平台。 但是，与针对一个平台 /ltcg: pginstrument 操作生成的.pgd 文件不是有效作为针对不同平台 /ltcg: pgoptimize 的输入。

若要解决此错误，仅传递使用 /ltcg: pginstrument 到 /ltcg: pgoptimize 同一平台上创建一个.pgd 文件。