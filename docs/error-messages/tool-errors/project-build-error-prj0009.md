---
title: "项目生成错误 PRJ0009 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0009
dev_langs: C++
helpviewer_keywords: PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ee183c24cf330b54a335efbd0bbe2b00e18d209
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0009"></a>项目生成错误 PRJ0009
生成日志无法打开以进行写入。  
  
 **请确保文件未被另一个进程打开，并且未被写保护。**  
  
 设置后**生成日志记录**属性**是**和执行生成或重新生成时，Visual c + + 程序无法以独占方式打开生成日志。  
  
 检查**生成日志记录**设置通过打开**选项**对话框 (上**工具**菜单上，单击**选项**命令)，然后选择**VC + + 生成**中**项目**文件夹。 生成文件称为 BuildLog.htm，并且会写入到中间目录 $(IntDir)。  
  
 此错误的可能原因：  
  
-   你将正在运行的 Visual c + + 的两个进程，并尝试同时生成的同一个项目中都相同的配置。  
  
-   生成日志文件是锁定了文件的进程中打开的。  
  
-   用户没有权限创建文件。  
  
-   当前用户没有写访问权限的文件的 BuildLog.htm。