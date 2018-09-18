---
title: BSCMAKE 错误 BK1509 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 091fab63737c7ee1b3b85753a354bb7214cfa411
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025238"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 错误 BK1509

堆空间不足

BSCMAKE 耗尽了内存，包括虚拟内存。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 释放一些磁盘空间。

1. 增加交换文件的大小。

1. 增加 Windows 交换文件的大小。

1. 减少使用 /Ei BSCMAKE 要求的内存或 /Es 以消除一些输入文件或/e m 以消除宏正文。