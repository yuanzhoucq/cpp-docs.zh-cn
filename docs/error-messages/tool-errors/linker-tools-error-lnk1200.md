---
title: 链接器工具错误 LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466828"
---
# <a name="linker-tools-error-lnk1200"></a>链接器工具错误 LNK1200

读取程序数据库 filename 时出错

无法读取程序数据库 (PDB)。

可以通过文件损坏导致此错误。

如果`filename`是在 PDB 有关对象文件，重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。

如果`filename`是主输出文件的 PDB 和增量链接期间出现此错误，删除 PDB 并重新链接。