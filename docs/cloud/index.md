---
title: "Visual C++ 中的云和 Web 编程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
caps.latest.revision: 13
caps.handback.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Visual C++ 中的云和 Web 编程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 中有多种选项可使你连接到 Web 和云。  
  
 [Microsoft Azure 移动服务](http://www.windowsazure.com/develop/mobile/)  
 提供可在 Windows 应用商店应用或 Windows 桌面应用中使用的本机 API，用于连接到 Microsoft Azure 移动服务。 虽然该网站上的大部分示例采用 C\# 编写，但也可以使用 C\+\+。 有关详细信息，请参阅[快速入门：使用 C\+\+ 添加移动服务](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx)。  
  
 [实时 REST 接口](http://msdn.microsoft.com/library/live/hh243648.aspx)  
 提供可在 Windows 应用商店应用、Windows 桌面应用或 C\+\+ Linux 应用程序中使用的 REST 终结点，用于连接到 [Live](http://msdn.microsoft.com/live/ff519582) 服务，如 SkyDrive、Outlook.com 和 Skype。 C\+\+ 应用直接使用这些终结点，而不是通过使用仅适用于 .NET 应用的 Live SDK。  
  
 [C\+\+ REST SDK \(Codename "Casablanca"\)](../top/cpp-rest-sdk-codename-casablanca.md)  
 提供便捷的异步 HTTP 包装器方法，该方法旨在实现跨平台兼容性以及用于回到 Windows 7 和 Windows Server 2012 的操作系统上的桌面应用。 也可在通用 Windows 平台应用中使用这些方法；但是，对于仅面向通用 Windows 平台的应用，我们建议你使用 `Windows::Web:HttpClient` 类。 C\+\+ REST SDK \(codename "Casablanca"\) 还提供了支持 REST 调用和将 JSON 数据转换为 C\+\+ 类型的帮助程序类。 该 SDK 在 [CodePlex](http://casablanca.codeplex.com/) 上可用，并且包含 [live\_connect.h](http://casablanca.codeplex.com/SourceControl/latest#Release/collateral/Samples/WindowsLiveAuth/live_connect.h) 等示例文件，该示例文件为连接到 [Live](http://msdn.microsoft.com/live/ff519582) 服务提供帮助器方法。  
  
 [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)  
 Windows 运行时 HTTP 客户端类在 .NET Framework 类上建模，后者在 System.Web 命名空间中具有相同的名称。`HttpClient` 完全支持通过 HTTP 异步上载和下载，还完全支持可将自定义 HTTP 处理程序插入到管道中的管道筛选器。 Windows SDK 包括用于按流量计费的网络和 OAuth 身份验证等的样本筛选器。  
  
 [IXMLHTTPRequest2 接口](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)  
 提供可在 Windows 应用商店应用或 Windows 桌面应用中使用的本机 COM 接口，用于通过 HTTP 连接到 Internet，并发布 GET、PUT 和其他 HTTP 命令。 有关详细信息，请参阅 [演练：使用任务和 XML HTTP 请求进行连接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。  
  
 [Windows Internet \(WinInet\)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)  
 可以在 Windows 桌面应用中使用以连接到 Internet 的 Windows API。  
  
## 请参阅  
 [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)   
 [连接到网络和 Web 服务（使用 C\#\/VB\/C\+\+ 和 XAML 的 Windows 应用商店应用）](http://msdn.microsoft.com/library/windows/apps/br229573.aspx)