---
title: 定义宏的位置 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf3e87a50362c770d45f00c4dc17ac3d264f611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="where-to-define-macros"></a>定义宏的位置
在命令行、 命令文件、 生成文件中，或 Tools.ini 文件中定义宏。  
  
 在生成文件或 Tools.ini 文件中，每个宏的定义必须出现在单独的行，并且不能以空格或制表符开头。忽略空格或等号两侧的选项卡。 所有[字符的字符串](../build/defining-an-nmake-macro.md)都是文本，包括周围的引号和嵌入的空格。  
  
 在命令行或命令文件中，空格和制表符分隔自变量，并不能出现在等号。 如果`string`有嵌入空格或制表符，将字符串本身或整个宏括在双引号 ("")。  
  
## <a name="see-also"></a>请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)