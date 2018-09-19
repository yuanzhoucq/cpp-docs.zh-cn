---
title: Tools.ini 和 NMAKE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723575"
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

NMAKE 读取 Tools.ini 之前读取生成文件，除非使用 /R。 它 Tools.ini 首先查找当前目录中，然后由 INIT 环境变量指定的目录中。 NMAKE 中的设置初始化文件的部分开头`[NMAKE]`，并且可以包含任何生成文件的信息。 以数字符号开头的单独的行上指定的注释 (）。

## <a name="see-also"></a>请参阅

[运行 NMAKE](../build/running-nmake.md)