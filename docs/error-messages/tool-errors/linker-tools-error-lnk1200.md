---
title: 链接器工具错误 LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195131"
---
# <a name="linker-tools-error-lnk1200"></a>链接器工具错误 LNK1200

读取程序数据库 "filename" 时出错

无法读取程序数据库（PDB）。

此错误可能是由文件损坏引起的。

如果 `filename` 是对象文件的 PDB，请使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)重新编译对象文件。

如果 `filename` 是主输出文件的 PDB，而在增量链接期间发生此错误，请删除 PDB 并重新链接。
