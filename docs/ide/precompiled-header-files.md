---
title: "预编译的头文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""stdafx.h""
  - "stdafx.h"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stdafx.h"
  - "PCH 文件, 文件说明"
  - ".pch 文件, 文件说明"
  - "预编译的头文件, 文件说明"
  - "stdafx.cpp"
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 预编译的头文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些文件用于对头文件 *Projname*.pch 和预编译的类型文件 Stdafx.obj 进行生成和预编译。  
  
 这些文件位于 *Projname* 目录中。 在解决方案资源管理器中，Stdafx.h 位于标头文件文件夹中，而 Stdafx.cpp 位于源文件文件夹中。  
  
|文件名|说明|  
|---------|--------|  
|Stdafx.h|标准系统的包含文件和项目特定的包含文件的包含文件，经常使用但不常更改。<br /><br /> 不应定义或取消定义 stdafx.h 中的任何 \_AFX\_NO\_XXX 宏；请参阅知识库文章“PRB：定义 \_AFX\_NO\_XXX 时出现的问题”。 可在 MSDN Library 或 [http:\/\/ support.microsoft.com\/](http://%20support.microsoft.com/) 上查找知识库文章。|  
|Stdafx.cpp|包含预处理器指令 `#include "stdafx.h"` 并添加预编译类型的包含文件。 任何类型的预编译文件（包括头文件）都可通过将编译仅限于有需要的文件，从而支持更快的编译时间。 首次生成项目后，你将注意到由于预编译头文件的存在，随后生成的生成时间将大大加快。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [如何：用属性页指定项目属性](../misc/how-to-specify-project-properties-with-property-pages.md)