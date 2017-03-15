---
title: "错误 C1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1010"
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 错误 C1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在查找预编译头时遇到意外的文件结尾。是否忘记了向源代码中添加“\#include name”?  
  
 用 [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 指定的包含文件没有列在源文件中。在大多数的 Visual C\+\+ 项目类型中，此选项默认是启用的，而且“stdafx.h”是此选项指定的默认包含文件。  
  
 在 Visual Studio 环境中，请使用下列方法之一消除此错误：  
  
-   如果项目中没有使用预编译头，请将源文件的**“创建\/使用预编译头”**属性设置为**“不使用预编译头”**。  若要设置此编译器选项，请遵循以下这些步骤：  
  
    1.  在项目的“解决方案资源管理器”窗格中，右击项目名称，再单击**“属性”**。  
  
    2.  在左窗格中单击“**C\/C\+\+**”文件夹。  
  
    3.  单击**“预编译头”**节点。  
  
    4.  在右窗格中单击**“创建\/使用预编译头”**，再单击**“不使用预编译头”**。  
  
-   确保您没有在不注意的情况下从当前项目中删除、重命名或移除头文件（默认为 stdafx.h）。  还需要使用 **\#include "stdafx.h"** 在源文件中的任何其他代码之前包含这一文件。（此头文件被指定为**“通过文件创建\/使用 PCH”**项目属性）