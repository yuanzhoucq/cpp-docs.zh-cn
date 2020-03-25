---
title: 链接器工具错误 LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183808"
---
# <a name="linker-tools-error-lnk1241"></a>链接器工具错误 LNK1241

已指定资源文件 "resource file"

如果从命令行手动运行**cvtres** ，然后将生成的 .obj 文件传递给链接器以及其他 res 文件，则会生成此错误。

若要指定多个 .res 文件，请将它们全部作为 .res 文件传递给链接器，而不是从**cvtres**创建的 .obj 文件中传递。
