---
title: 文件名部分语法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d807087be171a2ad63ed37a8b359c3200c812040
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367480"
---
# <a name="filename-parts-syntax"></a>文件名部分语法
在命令中的文件名部分语法表示第一个依赖项文件名 （它可能是暗含的依赖项） 的组件。 文件名组件文件的驱动器、 路径、 基名称和按指定的扩展名不是它存在于磁盘上。 使用 **%s**来表示完整的文件名。 使用 **%&#124;**[*部件*]**F** (竖线字符百分号后面跟着) 来表示部分文件名，其中*部件*可以为零个或多个以下的字母，按任何顺序排列。  
  
|Letter|描述|  
|------------|-----------------|  
|无号|完整名称 (与相同 **%s**)|  
|**d**|驱动器|  
|**p**|路径|  
|**f**|文件基名称|  
|**e**|文件扩展名|  
  
 例如，如果文件名为 c:\prog.exe:  
  
-   %s 将 c:\prog.exe  
  
-   %&#124;F 将 c:\prog.exe  
  
-   %&#124;dF 将 c  
  
-   %&#124;pF 将 c:\  
  
-   %&#124;fF 将 prog  
  
-   %&#124;eF 将 exe  
  
## <a name="see-also"></a>请参阅  
 [生成文件中的命令](../build/commands-in-a-makefile.md)