---
title: BSCMAKE 错误 BK1509
ms.date: 11/04/2016
f1_keywords:
- BK1509
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
ms.openlocfilehash: 384f202ea3eb969da2ce3a3b82209c383009c62e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279523"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 错误 BK1509

堆空间不足

BSCMAKE 耗尽了内存，包括虚拟内存。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 释放一些磁盘空间。

1. 增加交换文件的大小。

1. 增加 Windows 交换文件的大小。

1. 减少使用 /Ei BSCMAKE 要求的内存或 /Es 以消除一些输入文件或/e m 以消除宏正文。