---
title: 链接器工具警告 LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: f67990ed74f500f1b954edcf1d6437f64f93f0d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298602"
---
# <a name="linker-tools-warning-lnk4014"></a>链接器工具警告 LNK4014

无法找到成员对象"objectname"

找不到 LIB`objectname`库中。

**/Remove**并 **/extract**选项都要求将被删除或复制到文件的成员对象的完整名称。 全名包括原始对象文件的路径。 若要查看库中的成员对象的完整名称，请使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。