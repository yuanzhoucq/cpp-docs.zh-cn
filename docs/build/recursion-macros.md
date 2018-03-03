---
title: "递归宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8d9ef7f194151fb3259712759d0c29ed157d564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recursion-macros"></a>递归宏
递归宏用于 NMAKE 递归调用。 递归会话将继承命令行和环境变量宏和 Tools.ini 信息。 他们不继承生成文件定义的推理规则或**。后缀**和**。宝贵**规范。 要传递到递归 NMAKE 会话的宏，请设置环境变量使用 SET 递归调用之前，递归调用，该命令中定义的宏，或者在 Tools.ini 中定义的宏。  
  
|宏|定义|  
|-----------|----------------|  
|**请**|最初用于调用 NMAKE 命令。<br /><br /> $(MAKE) 宏赋予 nmake.exe 的完整路径。|  
|**MAKEDIR**|NMAKE 调用时的当前目录。|  
|**MAKEFLAGS**|当前正在生效的选项。 使用作为`/$(MAKEFLAGS)`。  请注意，/F 不包含。|  
  
## <a name="see-also"></a>请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)