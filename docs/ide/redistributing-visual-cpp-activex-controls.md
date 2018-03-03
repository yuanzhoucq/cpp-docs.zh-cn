---
title: "重新分发 Visual c + + ActiveX 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c520d365a259c36baab8edeb9049aab9ac89925a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-activex-controls"></a>重新分发 Visual C++ ActiveX 控件
Visual c + + 6.0 提供可以在你然后重新分发的应用程序中使用的 ActiveX 控件。 Visual c + + 中不再包含这些控件。 每个 Visual c + + 6.0 许可协议，你可以与在 Visual c + + 中开发的应用程序重新发布这些控件。  
  
> [!NOTE]
>  Microsoft 不再支持 visual c + + 6.0。  
  
 可再发行 Visual c + + 6.0 ActiveX 控件的列表，请参阅 Visual c + + 6.0 产品 CD 的光盘 1 上的 Common\Redist\Redist.txt。  
  
 当分发应用程序，你必须安装并注册 ActiveX 控件 （使用 Regsvr32.exe）.ocx。 此外，应确保目标计算机具有以下系统文件 （星号指示文件需要注册） 的当前版本：  
  
-   asycfilt.dll  
  
-   Comcat.dll *  
  
-   Oleaut32.dll *  
  
-   Olepro32.dll *  
  
-   stdole2.tlb  
  
 如果这些 Dll 不在目标系统上可用，你需要获取这些更新使用所规定的机制用于更新相应的操作系统。 你可以从 Windows 操作系统最新服务包下载[http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com)。  
  
 如果你的应用程序使用一个连接到数据库的 ActiveX 控件，你必须具有目标系统上安装 Microsoft 数据访问组件 (MDAC)。 有关详细信息，请参阅[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
 在使用连接到数据库的 ActiveX 控件，你还需要复制目标计算机上的数据源名称。 你可以使用执行此操作以编程方式函数如`ConfigDSN`。  
  
 某些可再发行的 ActiveX 控件有附加依赖项。 对于 Visual c + + 6.0 产品 CD 上 Os\System 文件夹中每个.ocx 文件，此外还有.dep 文件。 对于每个你想要重新分发的.ocx 文件，查找相应的.dep 文件中的一个或多个使用条目。 如果某个文件列出时，你必须确保该文件是目标计算机上。 任何直接支持.ocx 文件的 Dll，需要注册。 （对于成功的 Regsvr32.exe，目标计算机必须首先包含的所有控件以静态方式加载的 Dll。）此外，如果一个 DLL，它列出为依赖项也具有.dep 文件，Visual c + + 6.0 CD 上的 Os\System 文件夹中，你必须调查该.dep 文件以了解使用条目。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)