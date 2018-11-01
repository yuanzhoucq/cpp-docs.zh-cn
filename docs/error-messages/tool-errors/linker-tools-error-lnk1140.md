---
title: 链接器工具错误 LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482456"
---
# <a name="linker-tools-error-lnk1140"></a>链接器工具错误 LNK1140

程序数据库; 的模块太多链接时使用 /PDB: NONE

该项目包含超过 4096 个模块。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 重新链接使用[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。

1. 某些模块编译而不进行调试的信息。

1. 减少模块的数量。