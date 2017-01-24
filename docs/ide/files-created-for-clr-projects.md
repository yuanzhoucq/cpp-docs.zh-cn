---
title: "为 CLR 项目创建的文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET 应用程序, C++"
  - "Visual C++ 项目, CLR 编程"
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 为 CLR 项目创建的文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 Visual C\+\+ 模板创建项目时会创建一些文件，具体取决于所使用的模板。  下表列出了项目模板为 .NET Framework 项目创建的所有文件。  
  
|文件名|文件说明|  
|---------|----------|  
|AssemblyInfo.cpp|此文件包含用于修改项目的程序集元数据的信息，即特性、文件、资源、类型、版本信息、签名信息等。  有关更多信息，请参见[程序集概念](../Topic/Assembly%20Contents.md)。|  
|*projname*.asmx|一个文本文件，它引用封装了 XML Web services 功能的托管类。|  
|*projname*.cpp|Visual Studio 为您创建的主源文件和应用程序的入口点。  标识项目的 .dll 文件和项目命名空间。  在此文件中提供您自己的代码。|  
|*projname*.vsdisco|一个 XML 部署文件，它包含对描述 XML Web services 的其他资源的链接。|  
|*projname*.h|项目的主包含文件，包含所有声明、全局符号和其他头文件的 `#include` 指令。|  
|*projname*.sln|在开发环境中用来将项目的所有元素组织成一个解决方案的解决方案文件。|  
|*projname*.suo|在开发环境中使用的解决方案选项文件。|  
|*projname.vcxproj*|在开发环境内用来存储该项目的特定信息的项目文件。|  
|ReadMe.txt|说明文件，它使用由模板创建的实际文件名来描述项目中的每个文件。|