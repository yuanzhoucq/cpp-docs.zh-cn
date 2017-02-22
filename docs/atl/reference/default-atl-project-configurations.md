---
title: "默认 ATL 项目配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 默认配置"
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 默认 ATL 项目配置
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题将 Visual C\+\+ .NET 中的默认 ATL 项目配置与 Visual C\+\+ 6.0 中的默认项目配置进行比较。  
  
## Visual C\+\+ .NET 默认配置  
 在 Visual C\+\+ .NET 中，“ATL 项目向导”在默认情况下创建两个项目配置。  
  
### Visual C\+\+ .NET 配置  
  
|配置|字符集|ATL 的使用|  
|--------|---------|-------------|  
|Release|MBCS|DLL|  
|调试|MBCS|DLL|  
  
 可在**常规**选项卡下的**项目设置**对话框中更改**字符集**、**“ATL 的使用”**。  也可使用配置管理器添加您自己的配置。  有关详细信息，请参见[生成配置](../Topic/Understanding%20Build%20Configurations.md)。  
  
## 6.0 版默认配置  
 在 Visual C\+\+ 6.0 版中，ATL COM 应用程序向导（现名为“ATL 项目向导”）默认情况下创建六个项目配置。  这些配置是“Release”、“Debug”、Unicode 以及 CRT 和 ATL 设置的使用的变体。  需要时，可在 Visual C\+\+ .NET 中使用配置管理器复制所有这些配置。  
  
### 6.0 版配置  
  
|配置|字符集|ATL 的使用|  
|--------|---------|-------------|  
|调试|MBCS|Static|  
|Debug Unicode|UNICODE|Static|  
|Release Min Dependency|MBCS|Static|  
|Release Min Dependency Unicode|UNICODE|Static|  
|Release Min Size|MBCS|DLL|  
|Release Min Size Unicode|UNICODE|DLL|  
  
## 请参阅  
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [Configuration Manager Dialog Box](http://msdn.microsoft.com/zh-cn/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [在 Visual Studio 中构建应用程序](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)