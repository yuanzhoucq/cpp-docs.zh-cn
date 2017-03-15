---
title: "通用 Windows 应用 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通用 Windows 应用 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通用 Windows 平台 \(UWP\) 应用体现了一套设计原则，强调以针对不同设备上不同屏幕大小自动调整的内容为中心的简单用户界面。 可在 XAML 标记中创建 UI，并使用本机 C\+\+ 创建代码隐藏。 此外，还可创建可供以其他语言编写的 UWP 应用使用的组件 \(DLL\)。 UWP 应用的 API 图面是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，这是一个分解库，可提供各种操作系统服务。  
  
> [!NOTE]
>  有关在 C\+\+ 中开发 UWP 应用的大部分文档都位于[Windows 开发人员中心](http://go.microsoft.com/fwlink/p/?LinkId=255563)网站上。 本文中的一些链接可转到该网站。  
  
## 使用 C\+\+\/CX 的 UWP 应用  
  
|||  
|-|-|  
|[Visual C\+\+ 语言参考 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=255561)|描述简化了 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] API 的 C\+\+ 消耗并启用了基于异常的错误处理的扩展集。|  
|[生成应用程序和库 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=264858)|描述如何创建可从 C\+\+\/CX 应用或组件进行访问的 Dll 和静态库。|  
|[教程：使用 C\+\+ 创建第一个 Windows 应用商店应用](http://go.microsoft.com/fwlink/p/?LinkId=255556)|一个演练，介绍使用 C\+\+ 开发 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用的基本概念。 （尚未针对 Windows 10 上的 UWP 开发进行更新。）|  
|[使用 C\+\+ 的 Windows 应用商店应用路线图](http://go.microsoft.com/fwlink/p/?LinkId=255553)|提供指向有关使用 C\+\+ 开发 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用和游戏的文章的链接。|  
|[用 C\+\+ 创建 Windows 运行时组件](http://go.microsoft.com/fwlink/p/?LinkId=255559)|描述如何创建其他 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用和组件可以使用的 DLL。|  
|[开发游戏](http://go.microsoft.com/fwlink/p/?LinkId=255554)|介绍如何使用 DirectX 和 C\+\+ 来创建游戏。|  
  
## 使用 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] \([!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)]\) 的 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]应用  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供低级别的 COM 接口，ISO C\+\+ 代码可通过该接口在无异常的环境中访问 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。 在多数情况下，建议使用 C\+\+\/CX 替代 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 进行 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用开发。 有关 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的详细信息，请参阅 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## 请参阅  
 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)