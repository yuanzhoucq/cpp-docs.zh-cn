---
title: "命令修饰符 |Microsoft 文档"
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
- NMAKE program, command modifiers
- command modifiers
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 610725bf52522cd5041d2f6dcadb422bf942458a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-modifiers"></a>命令修饰符
你可以指定前面的命令，可以选择用空格或制表符分隔的一个或多个命令修饰符。 与命令一样，必须缩进修饰符。  
  
|修饰符|目标|  
|--------------|-------------|  
|@*命令*|禁止显示的命令。 不禁止显示由命令。 默认情况下，NMAKE 回显所有执行的命令。 使用 /S 来取消显示整个生成文件;使用**。无提示**禁止显示生成文件的一部分。|  
|**-**[`number` ]*命令*|关闭的错误检查*命令*。 默认情况下，当命令返回非零退出代码时，NMAKE 暂停。 If-`number`是使用，NMAKE 停止如果退出代码超过`number`。 空格或制表符不能出现之间短划线和*数。* 至少一个空格或制表符必须之间出现`number`和*命令*。 使用 /i 选项关闭错误检查整个生成文件;使用**。忽略**若要关闭的生成文件的一部分的错误检查。|  
|**!** *command*|执行*命令*每个依赖文件如果*命令*使用 **$ \* \***  （依赖项中的所有依赖文件） 或**$?** （所有依赖文件中更高版本的时间戳比目标的依赖关系）。|  
  
## <a name="see-also"></a>请参阅  
 [生成文件中的命令](../build/commands-in-a-makefile.md)