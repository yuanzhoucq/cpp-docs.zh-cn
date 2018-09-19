---
title: BSCMAKE 警告 BK4502 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4142993b3f4f5bda2b3e4ce322aa26d7beca8584
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056321"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502

被截断。SBR 文件不在文件名中的 i

更新期间指定了长度为零的.sbr 文件最初不是.bsc 文件的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 指定的文件名出错。

1. 已删除的文件。 (错误[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)结果。)

1. 文件已损坏，需要 BSCMAKE 可执行完整生成。