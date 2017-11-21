---
title: "Tools.ini 和 NMAKE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 638132f640fd342a752ec45541275178f6f26692
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE
NMAKE 读取 Tools.ini 之前它读取生成文件，除非使用 /R。 它查找 Tools.ini 首先当前目录中，然后由 INIT 环境变量指定的目录中。 NMAKE 中的设置初始化文件的部分开头`[NMAKE]`并且可以包含任何生成文件的信息。 以数字符号开头的单独的行上指定的注释 （#）。  
  
## <a name="see-also"></a>另请参阅  
 [运行 NMAKE](../build/running-nmake.md)