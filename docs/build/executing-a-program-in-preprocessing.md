---
title: "在预处理中执行程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a6b98d3c03d319c2da397f969f8adf1ec858f72c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="executing-a-program-in-preprocessing"></a>在预处理中执行程序
若要在预处理过程中使用命令的退出代码，请与任何参数，在方括号 ([]) 中指定的命令。 所有宏都扩展之前执行此命令。 NMAKE 替换命令的退出代码，以便可以在表达式中用来控制预处理命令规范。  
  
## <a name="see-also"></a>另请参阅  
 [生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)