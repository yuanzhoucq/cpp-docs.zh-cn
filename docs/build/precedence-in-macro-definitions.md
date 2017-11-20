---
title: "宏定义中的优先级 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a71f69f141e92e7134d6048de67301198a667c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="precedence-in-macro-definitions"></a>宏定义中的优先级
如果宏具有多个定义，NMAKE 使用优先级最高的定义。 以下列表显示优先级从高到最低的顺序：  
  
1.  在命令行上定义的宏  
  
2.  宏生成文件中定义，或包含文件  
  
3.  继承的环境变量宏  
  
4.  Tools.ini 文件中定义的宏  
  
5.  预定义的宏，如[CC](../build/command-macros-and-options-macros.md)和[AS](../build/command-macros-and-options-macros.md)  
  
 使用 /E 会导致从环境变量重写一个同名的生成文件宏继承的宏。 使用**！UNDEF**重写命令行。  
  
## <a name="see-also"></a>另请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)