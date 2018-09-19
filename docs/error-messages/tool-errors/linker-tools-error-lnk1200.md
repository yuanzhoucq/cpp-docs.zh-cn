---
title: 链接器工具错误 LNK1200 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059311"
---
# <a name="linker-tools-error-lnk1200"></a>链接器工具错误 LNK1200

读取程序数据库 filename 时出错

无法读取程序数据库 (PDB)。

可以通过文件损坏导致此错误。

如果`filename`是在 PDB 有关对象文件，重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。

如果`filename`是主输出文件的 PDB 和增量链接期间出现此错误，删除 PDB 并重新链接。