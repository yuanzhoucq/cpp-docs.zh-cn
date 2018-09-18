---
title: 链接器工具警告 LNK4014 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df0a3b6f30733413a0f27c0b8daa07394bb04b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023106"
---
# <a name="linker-tools-warning-lnk4014"></a>链接器工具警告 LNK4014

无法找到成员对象"objectname"

找不到 LIB`objectname`库中。

**/Remove**并 **/extract**选项都要求将被删除或复制到文件的成员对象的完整名称。 全名包括原始对象文件的路径。 若要查看库中的成员对象的完整名称，请使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。