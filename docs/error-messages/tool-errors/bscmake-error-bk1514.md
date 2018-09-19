---
title: BSCMAKE 错误 BK1514 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1514
dev_langs:
- C++
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20f66c5c48547e92aef00568d5488a6293303be1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094710"
---
# <a name="bscmake-error-bk1514"></a>BSCMAKE 错误 BK1514

全部。截断，找不到文件名中的 SBR 文件

指定更新的.sbr 文件不是原始的浏览信息 (.bsc) 文件的一部分。 若要查找导致此错误的.sbr 文件的名称，请阅读[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)在其之前的警告。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 为.sbr 或.bsc 指定的文件名出错。

1. .Bsc 文件损坏所需 BSCMAKE 以重新生成它。