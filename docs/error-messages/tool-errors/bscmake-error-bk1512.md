---
title: BSCMAKE 错误 BK1512 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1512
dev_langs:
- C++
helpviewer_keywords:
- BK1512
ms.assetid: 0a626ff3-63db-4797-abe4-31545ce2c2c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce429c0c4cf0300b3818a9be9d28fd03e95f5eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039850"
---
# <a name="bscmake-error-bk1512"></a>BSCMAKE 错误 BK1512

filename： 超出了容量

BSCMAKE 无法生成浏览信息文件，因为定义、 引用、 模块或其他信息的数量超过了限制。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 排除使用/e m、 /Es 或 /Ei 一些信息。

1. 省略 /Iu 选项。