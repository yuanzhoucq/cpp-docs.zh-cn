---
title: 链接器工具错误 LNK1277 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082506"
---
# <a name="linker-tools-error-lnk1277"></a>链接器工具错误 LNK1277

pgd (filename) 中找不到的对象记录

使用时[/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)，其中一个输入的.lib、 def 或.obj 文件的路径为不同于其它们时找到的 /ltcg: pginstrument 的路径。 这可能出在 LIB 环境变量中的更改后 /ltcg: pginstrument。 输入文件的完整路径存储在.pgd 文件。

/Ltcg: pgoptimize 要求输入是 /ltcg: pginstrument 阶段相同。

若要解决此警告，请执行以下操作：

- 运行 /ltcg: pginstrument、 重做所有测试运行，并运行 /ltcg: pgoptimize。

- 将 LIB 环境变量更改为运行 /ltcg: pginstrument 时。

不建议使用 /LTCG:PGUPDATE 解决 LNK1277。