---
title: NMAKE 错误 U1051 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3d3a14b75a30aa22bcc9faafb97a218051bb080
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045011"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 错误 U1051

内存不足

NMAKE 用尽了内存中，由于生成文件太大或太复杂，包括虚拟内存。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 释放一些磁盘空间。

1. 增加 Windows NT 分页文件或 Windows 交换文件的大小。

1. 如果仅使用生成文件的一部分，则将生成文件划分为单独的文件或使用 **！如果**预处理指令以限制 NMAKE 必须处理量。 **！如果**指令包含 **！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！其他** `IFDEF`，和 **！其他** `IFNDEF`。