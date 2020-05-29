---
title: BSCMAKE 错误 BK1514
ms.date: 11/04/2016
f1_keywords:
- BK1514
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
ms.openlocfilehash: 14f74bba69db5bf3e02aecedd4540ef8a90d576b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197621"
---
# <a name="bscmake-error-bk1514"></a>BSCMAKE 错误 BK1514

一切.已截断 .SBR 文件，文件名中未找到任何内容

不是为更新指定的任何 .sbr 文件都是原始浏览信息（.bsc）文件的一部分。 若要查找导致此错误的 .sbr 文件的名称，请阅读其前面的[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)警告。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 为 .sbr 或 .bsc 指定了错误文件名。

1. 受损的 .bsc 文件需要 BSCMAKE 才能重新生成它。
