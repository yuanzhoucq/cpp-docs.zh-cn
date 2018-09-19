---
title: 链接器工具错误 LNK1140 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f850360bc749a41e548cebae9f58f9fc7d3d420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044699"
---
# <a name="linker-tools-error-lnk1140"></a>链接器工具错误 LNK1140

程序数据库; 的模块太多链接时使用 /PDB: NONE

该项目包含超过 4096 个模块。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 重新链接使用[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。

1. 某些模块编译而不进行调试的信息。

1. 减少模块的数量。