---
title: BSCMAKE 错误 BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: b272a12e1d729e33794b550c911fd2e56f1af006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197790"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 错误 BK1506

无法打开文件 "filename" [： reason]

BSCMAKE 无法打开该文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 文件被另一个进程锁定。 如果 `reason` 显示 "**权限被拒绝**"，则表示浏览器可能会使用该文件。 关闭 "浏览" 窗口，然后重试生成。

1. 完整磁盘。

1. 硬件错误。

1. 指定的输出文件的名称与现有子目录的名称相同。
