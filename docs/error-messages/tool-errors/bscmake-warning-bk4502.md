---
title: BSCMAKE 警告 BK4502
ms.date: 11/04/2016
f1_keywords:
- BK4502
- BK1513
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
ms.openlocfilehash: 34b0204744b390ac32371ff2611e43b215dc0f40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596347"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502

被截断。SBR 文件不在文件名中的 i

更新期间指定了长度为零的.sbr 文件最初不是.bsc 文件的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 指定的文件名出错。

1. 已删除的文件。 (错误[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)结果。)

1. 文件已损坏，需要 BSCMAKE 可执行完整生成。