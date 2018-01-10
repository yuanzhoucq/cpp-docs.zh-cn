---
title: "运行 NMAKE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6c39612cf4df47665f7ea3d529b77ee4e70ce8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="running-nmake"></a>运行 NMAKE
## <a name="syntax"></a>语法  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## <a name="remarks"></a>备注  
 仅指定 NMAKE 生成*目标*或如果未指定，第一个目标中生成文件。 第一个的生成文件目标可以是[伪目标](../build/pseudotargets.md)生成其他目标。 NMAKE 使用 /F; 使用指定的生成文件如果未指定 /F，它会使用当前目录中的生成文件文件。 如果指定不生成文件，则它使用推理规则来生成命令行*目标*。  
  
 `commandfile`文本文件 （或响应文件） 包含命令行输入。 其他输入可以前面或后面`commandfile`。 允许的路径。 在`commandfile`，分行符将被视为空格。 宏定义用引号引起来，如果它们包含空格。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [NMAKE 选项](../build/nmake-options.md)  
  
 [Tools.ini 和 NMake](../build/tools-ini-and-nmake.md)  
  
 [从 NMAKE 退出代码](../build/exit-codes-from-nmake.md)  
  
## <a name="see-also"></a>请参阅  
 [NMAKE 参考](../build/nmake-reference.md)