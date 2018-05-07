---
title: 重新分发 ATL 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c824dd4ae174a4418c6744e592dd62dc54b9595
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-an-atl-application"></a>重新分发 ATL 应用程序
从 Visual Studio 2012 开始，活动模板库 (ATL) 是仅包含标头的库。 ATL 项目没有指向 ATL 选项的动态链接。 不需要任何可再发行 ATL 库。  
  
 如果再次发行 ATL 可执行应用程序，必须通过发出以下命令来注册 .exe 文件（以及它所包含的任何控件）：  
  
```  
filename /regserver  
```  
  
 其中，`filename` 是可执行文件的名称。  
  
 在 Visual Studio 2010 中，可以为 MinDependency 或 MinSize 配置生成 ATL 项目。 MinDependency 配置是设置时获取的内容**ATL 的使用**属性**静态链接到 ATL**上**常规**属性页并设置**运行时库**属性**多线程 (/ MT)** 上**代码生成**属性页 （C/c + + 文件夹）。  
  
 MinSize 配置是设置时获取的内容**ATL 的使用**属性**动态链接到 ATL**上**常规**属性页中或一组**运行时库**属性**多线程 DLL (/ MD)** 上**代码生成**属性页 （C/c + + 文件夹）。  
  
 MinSize 使输出文件尽可能小，但要求 ATL100.dll 和 Msvcr100.dll (如果你选择**多线程 DLL (/ MD)** 选项) 的目标计算机上。 应在目标计算机上注册 ATL100.dll，以确保具有所有 ATL 功能。 ATL100.dll 包含 ANSI 和 Unicode 导出。  
  
 针对 MinDependency 目标生成 ATL 或 OLE DB 模板项目时，不需要在目标计算机上安装和注册 ATL100.dll，尽管可能获得更大的程序映像。  
  
 如果再次发行 ATL 可执行应用程序，必须通过发出以下命令来注册 .exe 文件（以及它所包含的任何控件）：  
  
```  
filename /regserver  
```  
  
 其中，`filename` 是可执行文件的名称。  
  
 对于 OLE DB 模板应用程序，确保目标计算机具有最新版本的 Microsoft 数据访问组件 (MDAC) 文件。 有关详细信息，请参阅[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)