---
title: "应用程序设置，ATL 项目向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.atl.com.appset
dev_langs: C++
helpviewer_keywords: ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12b7e383716d7cfa330bdfdebe21c33550669cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-atl-project-wizard"></a>应用程序设置，ATL 项目向导
使用**应用程序设置**ATL 项目向导设计并将基本功能添加到新的 ATL 项目页。  
  
## <a name="server-type"></a>服务器类型  
 选择三种服务器类型之一：  
  
 **动态链接库 (DLL)**  
 选择要创建一个进程内服务器。  
  
 **可执行文件 (EXE)**  
 选择创建的本地进程外服务器。 此选项不允许对 MFC 或 COM + 1.0 的支持。 它不允许为合并代理/存根代码。  
  
 **服务 (EXE)**  
 选择创建的 Windows 应用程序在 Windows 启动时在后台运行。 此选项不允许支持 MFC 或 COM + 1.0，或不允许合并代理/存根代码。  
  
## <a name="additional-options"></a>附加选项  
  
> [!NOTE]
>  所有其他选项都仅适用于 DLL 项目。  
  
 **允许合并代理/存根代码**  
 选择**允许合并代理/存根代码**为方便起见需要封送接口时的复选框。 此选项将在相同的 MIDL 生成的代理和存根代码可执行文件作为服务器。  
  
 **MFC 支持**  
 选择此选项可以指定你的对象包括 MFC 支持。 此选项将项目链接到 MFC 库，以便你可以访问的任何类和它们所包含的功能。  
  
 **支持 COM + 1.0**  
 选择此选项可修改项目的生成设置来支持 COM + 1.0 组件。 除了标准库的列表，则向导将添加 COM + 1.0 特定于组件的库 comsvcs.lib  
  
 此外，mtxex.dll 是你的应用程序启动时加载主机系统上的延迟。  
  
-   **支持组件注册机构**如果 ATL 项目包含对 COM + 1.0 组件的支持，则可以设置此选项。 组件注册机构允许你 COM + 1.0 对象获取组件的列表、 注册组件，或注销组件 （单独或在一次）。  
  
## <a name="see-also"></a>请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

