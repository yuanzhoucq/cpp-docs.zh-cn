---
title: 错误 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203354"
---
# <a name="fatal-error-c1305"></a>错误 C1305

配置文件数据库 "pgd_file" 适用于不同的体系结构

向[/ltcg： PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)传递了从另一个平台的/LTCG： PGINSTRUMENT 操作生成的 .pgd 文件。 [按配置优化](../../build/profile-guided-optimizations.md)适用于 x86 和 x64 平台。 但是，对于一个平台，为/LTCG： PGINSTRUMENT 操作生成的 .pgd 文件对于不同平台的/LTCG： PGOPTIMIZE 的输入无效。

若要解决此错误，请仅在同一平台上将使用/LTCG： PGINSTRUMENT 创建的 .pgd 文件传递给/LTCG： PGOPTIMIZE。
