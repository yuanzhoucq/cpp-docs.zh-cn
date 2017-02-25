---
title: "项目生成错误 PRJ0003 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0003"
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 项目生成错误 PRJ0003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成“command line”时出错。  
  
 由**“属性页”**对话框中的用户输入形成的命令 ***command line*** 返回了一个错误代码，但输出窗口中不显示任何信息。  
  
 此错误的可能原因为：  
  
-   项目依赖于 ATL Server。  从 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 开始，ATL Server 不再包括在 Visual Studio 中，但已在 CodePlex 作为共享源代码项目发布。  若要下载 ATL Server 源代码和工具，请转到[http:\/\/go.microsoft.com\/fwlink\/?LinkID\=81979](http://go.microsoft.com/fwlink/?LinkID=81979)。  
  
-   系统资源不足。  关闭一些应用程序以解决此问题。  
  
-   没有足够的安全特权。  验证是否有足够的安全特权。  
  
-   [VC\+\+ 目录](http://msdn.microsoft.com/zh-cn/e027448b-c811-4c3d-8531-4325ad3f6e02)中指定的可执行路径不包括您正尝试运行的工具的路径。  
  
-   对于生成文件项目，缺少要在**“生成命令行”**或**“重新生成命令行”**上运行的命令。  
  
## 请参阅  
 [项目生成错误和警告 \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)