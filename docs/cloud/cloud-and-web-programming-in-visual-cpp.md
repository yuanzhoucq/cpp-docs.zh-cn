---
title: 云和 Web 编程的 Visual c + + |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-azure
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f946a0e24790fd894e4eb908e77163306130e46a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214631"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Visual C++ 中的云和 Web 编程

C++ 中有多种选项可使你连接到 Web 和云。

## <a name="cloud-programming-options"></a>云编程的选项

- [Microsoft Azure 移动服务](http://www.windowsazure.com/develop/mobile/)

   提供的本机 Api，可以使用通用 Windows 平台 (UWP) 应用或 Windows 桌面应用中连接到 Windows Azure 移动服务。 虽然该网站上的大部分示例采用 C# 编写，但也可以使用 C++。 有关详细信息，请参阅[快速入门： 使用 c + + 的移动服务中添加](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx)。

- [C + + 的 Microsoft Azure 存储客户端库](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

   用于 c + + 的 Azure 存储客户端库提供全面的 API 使用 Azure 存储，包括但不是限于以下功能：

  - 创建、 读取、 删除和列出 blob 容器、 表和队列。
  - 创建、 读取、 删除、 列表和复制 blob 加上读取和写入 blob 范围。
  - 插入、 删除、 替换、 合并和 Azure 表中的查询实体。
  - 排队和取消排队中 Azure 队列的消息。
  - 延迟列出容器、 blob、 表和队列，并延迟查询实体

- [OneDrive API](https://dev.onedrive.com/README.htm)

   OneDrive API 提供了一组 HTTP 服务以应用程序连接到 Office 365 和 SharePoint Server 2016 中文件和文件夹。

- [C++ REST SDK (Codename "Casablanca")](https://github.com/Microsoft/cpprestsdk)

   提供一个新式、 跨平台的异步 API 与 REST 服务进行交互。

  - 执行对任何 HTTP 服务器，对分析的 JSON 文档和序列化的内置支持 REST 调用
  - 支持 OAuth 1 和 2，包括本地重定向侦听器
  - 建立 Websocket 连接针对远程服务
  - 完全异步任务基于 PPL，包括内置的线程池 API

   支持 Windows 桌面 （7 +）、 Windows Server （2012年 +）、 通用 Windows 平台、 Linux、 OSX、 Android 和 iOS。 

- [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/library/windows/apps/windows.web.http.httpclient.aspx)

   Windows 运行时 HTTP 客户端类在 .NET Framework 类上建模，后者在 System.Web 命名空间中具有相同的名称。 `HttpClient` 完全支持通过 HTTP 异步上载和下载，还完全支持可将自定义 HTTP 处理程序插入到管道中的管道筛选器。 Windows SDK 包括用于按流量计费的网络和 OAuth 身份验证等的样本筛选器。 对于面向通用 Windows 平台的应用，我们建议你使用`Windows::Web:HttpClient`类。 

- [IXMLHTTPRequest2 接口](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

   提供的本机 COM 接口，可以使用 Windows 运行时的应用或 Windows 桌面应用程序中通过 HTTP 连接到 Internet 并发布 GET、 PUT 和其他 HTTP 命令。 有关详细信息，请参阅[演练： 使用任务和 XML HTTP 请求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

- [Windows Internet (WinInet)](https://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)

   可以在 Windows 桌面应用中使用以连接到 Internet 的 Windows API。

## <a name="see-also"></a>请参阅

[Visual C++](../visual-cpp-in-visual-studio.md) <br/>
[网络和 web 服务](/windows/uwp/networking/)
