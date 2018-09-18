---
title: 错误 C1305 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4beb1140d161b8cbe54cab40dcc72899c976edc3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048742"
---
# <a name="fatal-error-c1305"></a>错误 C1305

配置文件数据库 pgd_file 是用于不同的体系结构

另一个平台已传递给从 /ltcg: pginstrument 操作生成一个.pgd 文件[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [按配置优化](../../build/reference/profile-guided-optimizations.md)可用于 x86 和 x64 平台。 但是，与针对一个平台 /ltcg: pginstrument 操作生成的.pgd 文件不是有效作为针对不同平台 /ltcg: pgoptimize 的输入。

若要解决此错误，仅传递使用 /ltcg: pginstrument 到 /ltcg: pgoptimize 同一平台上创建一个.pgd 文件。