---
title: Tools.ini 和 NMAKE |Microsoft 文档
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
ms.openlocfilehash: 860a334274a3a1a4ac9e11c3e7b5e9a0f136ecc0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE
NMAKE 读取 Tools.ini 之前它读取生成文件，除非使用 /R。 它查找 Tools.ini 首先当前目录中，然后由 INIT 环境变量指定的目录中。 NMAKE 中的设置初始化文件的部分开头`[NMAKE]`并且可以包含任何生成文件的信息。 以数字符号开头的单独的行上指定的注释 （#）。  
  
## <a name="see-also"></a>请参阅  
 [运行 NMAKE](../build/running-nmake.md)