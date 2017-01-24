---
title: "演练：使用任务和 XML HTTP 请求进行连接 | Microsoft Docs"
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
helpviewer_keywords: 
  - "连接到 Web 服务, Windows 应用商店应用 [C++]"
  - "IXMLHTTPRequest2 和任务, 示例"
  - "IXHR2 和任务, 示例"
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：使用任务和 XML HTTP 请求进行连接
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

演示如何将 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-cn/bbc11c4a-aecf-4d6d-8275-3e852e309908) 和 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-cn/aa4b3f4c-6e28-458b-be25-6cce8865fc71) 接口与任务结合使用，以将 HTTP GET 和 POST 请求发送至 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用中的 Web 服务。  整合 `IXMLHTTPRequest2` 的任务， 您能够组合其他任务来写代码。  例如，作为任务的一部分，链可以使用下载任务。  工作的时间时，下载任务还可以响应。  
  
> [!TIP]
>  还可以使用 C\+\+ 其他 SDK 从 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app 使用 C\+\+ app 或从桌面 C\+\+ 应用程序执行 HTTP 请求。  有关更多信息，请参见 [C\+\+ REST SDK \(Codename "Casablanca"\)](../../top/cpp-rest-sdk-codename-casablanca.md)。  
  
 有关任务的更多信息，请参见 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  有关如何在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 中使用媒体文件的详细信息，请参阅[Asynchronous programming in C\+\+](http://msdn.microsoft.com/zh-cn/512700b7-7863-44cc-93a2-366938052f31)和[用 C\+\+ 为 Windows 应用商店应用程序创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
  
 文档第一个演示如何创建 `HttpRequest` 及其支持的选件类。  然后演示如何使用 C\+\+ 和 XAML 从 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app 使用此类。  
  
 对于使用的更完整示例 `HttpReader` 选件类中描述的文档，请参见 [在 JavaScript 和 C\+\+ 中开发 Windows 应用商店应用程序 Bing 地图行程优化器](../Topic/Developing%20Bing%20Maps%20Trip%20Optimizer,%20a%20Windows%20Store%20app%20in%20JavaScript%20and%20C++.md)。  有关使用其中`IXMLHTTPRequest2`许多特性的示例但没有使用任务，请参见 [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/zh-cn/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)。  
  
> [!TIP]
>  `IXMLHTTPRequest2` 和 `IXMLHTTPRequest2Callback` 是建议用于 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app 的接口。  还可以满足此示例用于桌面应用程序。  
  
## 系统必备  
  
## 定义 HttpRequest、HttpRequestBuffersCallback 和 HttpRequestStringCallback 类  
 当您使用 `IXMLHTTPRequest2` 接口创建在 HTTP 时的 web 请求，则实现 `IXMLHTTPRequest2Callback` 接口接收服务器答复和响应到其他活动。  此示例定义 `HttpRequest` 选件类创建 web 请求和 `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 选件类处理响应。  `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 选件类支持 `HttpRequest` 选件类；您只能使用从应用程序代码的 `HttpRequest` 选件类一起使用。  
  
 `GetAsync`，`HttpRequest` 选件类的 `PostAsync` 方法可以启动 HTTP GET 和 POST 操作，分别。  这些方法使用 `HttpRequestStringCallback` 选件类读取服务器响应以字符串。  `SendAsync` 和 `ReadAsync` 方法允许您对区块的流用内容。  上述每种方法返回 [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 表示运算。  `GetAsync` 和 `PostAsync` 方法产生 `task<std::wstring>` 值，`wstring` 部件表示该服务器的响应。  `SendAsync` 和 `ReadAsync` 方法产生 `task<void>` 值；这些任务完成，当完成发送和读取操作。  
  
 因为`IXMLHTTPRequest2`接口异步操作，该示例使用[concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md)创建完成回调对象完成或取消下载操作后的任务。  `HttpRequest` 选件类创建从此任务的基于任务的延续设置最终结果。  `HttpRequest` 选件类使用基于任务的延续确保延续任务运行，即使前面的任务会导致错误或取消。  有关延续的更多信息，请参见 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 若要支持取消，`HttpRequest`、`HttpRequestBuffersCallback`和 `HttpRequestStringCallback` 选件类使用取消标记。  `HttpRequestBuffersCallback` 和 `HttpRequestStringCallback` 选件类使用 [concurrency::cancellation\_token::register\_callback](../Topic/cancellation_token::register_callback%20Method.md) 方法使任务完成事件时响应取消。  此移除回调中止下载。  有关取消操作的更多信息，请参见 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
#### 定义 HttpRequest 类  
  
1.  使用 Visual C\+\+ “空白应用程序 \(XAML\)” 模板创建空白 XAML 应用程序项目。  此示例将项目命名为`UsingIXMLHTTPRequest2`。  
  
2.  向项目添加名为 HttpRequest.h 和源文件名为 HttpRequest.cpp 的一个标头文件。  
  
3.  在 pch.h，添加以下代码：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#1](concrt-using-IXMLHTTPRequest2#1)]  
  
4.  在 HttpRequest.h，添加以下代码：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#2](concrt-using-IXMLHTTPRequest2#2)]  
  
5.  在 HttpRequest.h，添加以下代码：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#3](concrt-using-IXMLHTTPRequest2#3)]  
  
## 在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用 HttpRequest 类  
 本节中 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app 演示如何使用 `HttpRequest` 选件类。  该应用程序提供定义了一个 URL 资源的框中，输入，并执行获取和发布操作的命令按钮并取消当前操作的按钮命令。  
  
#### 使用 HttpRequest 类  
  
1.  在 MainPage.xaml，如下所示请定义元素 [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx)。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A1](concrt-using-IXMLHTTPRequest2#A1)]  
  
2.  在 MainPage.xaml.h，请将此 `#include` 指令：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A2](concrt-using-IXMLHTTPRequest2#A2)]  
  
3.  在 MainPage.xaml.h，请将这些 `private` 成员变量。`MainPage` 选件类：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A3](concrt-using-IXMLHTTPRequest2#A3)]  
  
4.  在 MainPage.xaml.h，声明 `private` 方法 `ProcessHttpRequest`:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A4](concrt-using-IXMLHTTPRequest2#A4)]  
  
5.  在 MainPage.xaml.cpp，请将这些 `using` 语句：  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A5](concrt-using-IXMLHTTPRequest2#A5)]  
  
6.  在 MainPage.xaml.cpp，请实现 `GetButton_Click`，`PostButton_Click`，并且，`MainPage` 的 `CancelButton_Click` 方法类别。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A6](concrt-using-IXMLHTTPRequest2#A6)]  
  
    > [!TIP]
    >  如果您的应用程序不需要取消支持，通过 [concurrency::cancellation\_token::none](../Topic/cancellation_token::none%20Method.md) 到 `HttpRequest::GetAsync` 和 `HttpRequest::PostAsync` 方法。  
  
7.  在 MainPage.xaml.cpp，请执行 `MainPage::ProcessHttpRequest` 方法。  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A7](concrt-using-IXMLHTTPRequest2#A7)]  
  
8.  在项目属性，在 “链接器”下，“输入”，指定 `shcore.lib` 和 `msxml6.lib`。  
  
 这是运行的应用程序：  
  
 ![运行的 Windows 应用商店应用](../../parallel/concrt/media/concrt_usingixhr2.png "ConcRT\_UsingIXHR2")  
  
## 后续步骤  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## 请参阅  
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Asynchronous programming in C\+\+](http://msdn.microsoft.com/zh-cn/512700b7-7863-44cc-93a2-366938052f31)   
 [用 C\+\+ 为 Windows 应用商店应用程序创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/zh-cn/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [task 类（并发运行时）](../../parallel/concrt/reference/task-class-concurrency-runtime.md)   
 [task\_completion\_event 类](../../parallel/concrt/reference/task-completion-event-class.md)   
 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-cn/bbc11c4a-aecf-4d6d-8275-3e852e309908)   
 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-cn/aa4b3f4c-6e28-458b-be25-6cce8865fc71)