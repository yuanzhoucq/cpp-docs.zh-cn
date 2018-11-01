---
title: BSCMAKE 错误 BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: d1f74a90657985a87accc13bc2b576c1d7fd5a4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554695"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 错误 BK1506

无法打开文件 filename [: 原因]

BSCMAKE 无法打开文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 另一个进程锁定的文件。 如果`reason`说**权限被拒绝**，浏览器可能正在使用该文件。 关闭浏览窗口，然后重试生成。

1. 磁盘已满。

1. 硬件错误。

1. 指定的输出文件具有与现有子目录相同的名称。