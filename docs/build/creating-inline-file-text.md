---
title: "创建内联文件文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 174160657e5494f5566fd0828815b3c0f1b3d601
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-inline-file-text"></a>创建内联文件文本
内联文件可以是临时的还是永久。  
  
## <a name="syntax"></a>语法  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>备注  
 指定*inlinetext*在命令后的第一行上。 在单独一行的开头用两个尖括号 (<<) 标记末尾。 该文件包含所有*inlinetext*之前分隔括号。 *Inlinetext*可以为宏扩展和替换，但不是指令或生成文件注释。 原义处理空格、 制表符和换行符。  
  
 临时文件的会话期间存在，并可以由其他命令重复使用。 指定**保留**右尖括号 NMAKE 会话中; 后保留文件后未命名的文件将保留在磁盘上生成的文件名。 指定**NOKEEP**或 nothing 为临时文件。 **保留**和**NOKEEP**不区分大小写。  
  
## <a name="see-also"></a>另请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)