---
title: 链接器工具错误 LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183652"
---
# <a name="linker-tools-error-lnk1277"></a>链接器工具错误 LNK1277

在 pgd （filename）中找不到对象记录

当使用[/ltcg： PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)时，其中一个输入 .lib、.def 或 .obj 文件的路径与在/LTCG： PGINSTRUMENT 中找到这些文件的路径不同。 在/LTCG： PGINSTRUMENT 后，可通过更改 LIB 环境变量中的内容来说明这一点。 输入文件的完整路径存储在 .pgd 文件中。

/LTCG： PGOPTIMIZE 要求输入与/LTCG： PGINSTRUMENT 阶段完全相同。

若要解决此警告问题，请执行以下操作之一：

- 运行/LTCG： PGINSTRUMENT，重做所有测试运行，并运行/LTCG： PGOPTIMIZE。

- 将 LIB 环境变量更改为运行/LTCG： PGINSTRUMENT 时的变量。

建议不要使用/LTCG： PGUPDATE 来解决 LNK1277。
