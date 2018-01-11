---
title: "项目生成错误 PRJ0003 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0003
dev_langs: C++
helpviewer_keywords: PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bcf80eb4d45fe1ae163772b96339c123996ae377
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="project-build-error-prj0003"></a>项目生成错误 PRJ0003  
  
> 错误生成*命令行*。  
  
*命令行*命令格式中的输入从**属性页**对话框返回错误代码，但没有信息将出现在**输出**窗口。  

此错误的可能原因包括：  
  
-   你的项目依赖于 ATL Server。 从 Visual Studio 2008 开始，ATL Server 不再的 Visual Studio 的一部分，但作为 CodePlex 上的共享源项目已释放。 若要下载的 ATL Server 源代码和工具，请转到[ATL 服务器库和工具](http://go.microsoft.com/fwlink/p/?linkid=81979)。  
  
-   系统资源不足。 关闭一些应用程序来解决此问题。  
  
-   没有足够的安全权限。 验证具有足够的安全特权。  
  
-   中指定的可执行文件路径**VC + + 目录**不包括正尝试运行该工具的路径。 有关信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)  
  
-   对于生成文件项目缺少上运行的命令**生成命令行**或**重新生成命令行**。  
  
## <a name="see-also"></a>请参阅  
 [项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)