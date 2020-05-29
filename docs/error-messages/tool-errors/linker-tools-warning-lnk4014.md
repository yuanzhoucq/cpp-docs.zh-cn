---
title: 链接器工具警告 LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194273"
---
# <a name="linker-tools-warning-lnk4014"></a>链接器工具警告 LNK4014

找不到成员对象 "objectname"

LIB 在库中找不到 `objectname`。

**/Remove**和 **/EXTRACT**选项要求要删除或复制到文件的成员对象的完整名称。 全名包括原始对象文件的路径。 若要查看库中成员对象的完整名称，请使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。
