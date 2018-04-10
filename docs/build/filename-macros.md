---
title: 文件名宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2073e4fcb365b3beb10d4040c0f54d9f61a0431
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="filename-macros"></a>文件名宏
文件名宏被预定义为依赖项 （在磁盘上的不完整的文件名规范） 中指定的文件名。 这些宏不需要括在圆括号中时调用;指定仅的 $ 所示。  
  
|宏|含义|  
|-----------|-------------|  
|**$@**|当前目标的完整名称 （路径、 基名称、 扩展），当前所指定。|  
|**$$@**|当前目标的完整名称 （路径、 基名称、 扩展），当前所指定。 仅在作为依赖项中有效。|  
|**$\***|当前目标的路径和基名称，去掉文件扩展名。|  
|**$\*\***|当前的目标的所有依赖项。|  
|**$?**|更高版本的时间戳比当前目标的所有依赖项。|  
|**$<**|具有更高版本的时间戳比当前的目标的依赖文件。 仅在推理规则中的命令中有效。|  
  
 若要指定预定义的文件名宏的一部分，追加宏修饰符，并将修改后的宏括在括号中。  
  
|修饰符|生成的文件名部分|  
|--------------|-----------------------------|  
|**D**|驱动器和目录|  
|**B**|基名称|  
|**F**|基名称和扩展名|  
|**R**|驱动器、 目录和基名称|  
  
## <a name="see-also"></a>请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)