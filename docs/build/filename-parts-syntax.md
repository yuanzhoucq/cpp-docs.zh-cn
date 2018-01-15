---
title: "文件名部分语法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a481f8c461cb4fddd4acb090edb2f2b5fd18636d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="filename-parts-syntax"></a>文件名部分语法
在命令中的文件名部分语法表示第一个依赖项文件名 （它可能是暗含的依赖项） 的组件。 文件名组件文件的驱动器、 路径、 基名称和按指定的扩展名不是它存在于磁盘上。 使用**%s**来表示完整的文件名。 使用**%&#124;**[*部件*]**F** (竖线字符百分号后面跟着) 来表示部分文件名，其中*部件*可以为零个或多个以下的字母，按任意顺序。  
  
|Letter|描述|  
|------------|-----------------|  
|无号|完整名称 (与相同**%s**)|  
|**d**|驱动器|  
|**p**|路径|  
|**f**|文件基名称|  
|**e**|文件扩展名|  
  
 例如，如果文件名为 c:\prog.exe:  
  
-   %s 将 c:\prog.exe  
  
-   %&#124;将 c:\prog.exe F。  
  
-   %&#124; dF 将 c  
  
-   %&#124; pF 将 c:\  
  
-   %&#124; fF 将 prog  
  
-   %&#124; eF 将 exe  
  
## <a name="see-also"></a>请参阅  
 [生成文件中的命令](../build/commands-in-a-makefile.md)