---
title: Tools.ini 和 NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317674"
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

NMAKE 读取 Tools.ini 之前读取生成文件，除非使用 /R。 它 Tools.ini 首先查找当前目录中，然后由 INIT 环境变量指定的目录中。 NMAKE 中的设置初始化文件的部分开头`[NMAKE]`，并且可以包含任何生成文件的信息。 以数字符号开头的单独的行上指定的注释 (）。

## <a name="see-also"></a>请参阅

[运行 NMAKE](running-nmake.md)
