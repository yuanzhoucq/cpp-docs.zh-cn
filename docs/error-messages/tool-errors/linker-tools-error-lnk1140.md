---
title: 链接器工具错误 LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195261"
---
# <a name="linker-tools-error-lnk1140"></a>链接器工具错误 LNK1140

程序数据库的模块太多;与/PDB： NONE 链接

项目包含4096个以上的模块。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 使用[/pdb： NONE](../../build/reference/pdb-use-program-database.md)进行重新链接。

1. 编译某些模块而不调试信息。

1. 减少模块的数量。
