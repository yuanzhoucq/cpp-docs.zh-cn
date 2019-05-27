---
title: Visual C++ 中的云和 Web 编程
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 677e9da18e8d171f523994d21bfbd0411270e3c8
ms.sourcegitcommit: bc1b14f29a02685f97c7ef5c098d16db6eaf369f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65790364"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Visual C++ 中的云和 Web 编程

C++ 中有多种选项可使你连接到 Web 和云。

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure SDK 和 REST 服务

- [用于 C++ 的 Microsoft Azure 存储客户端库](https://azure.github.io/azure-storage-cpp/)

  用于 C++ 的 Azure 存储客户端库提供了一个用于处理 Azure 存储的综合 API，此 API 包括但不限于以下功能：

  - 创建、读取、删除和列出 Blob 容器、表和队列。
  - 创建、读取、删除、列出和复制 Blob，以及读取和写入 Blob 范围。
  - 在 Azure 表中插入、删除、替换、合并和查询实体。
  - 在 Azure 队列中对消息进行排队和取消排队。
  - 延迟列出容器、Blob、表和队列，并延迟查询实体

- 用于物联网的 ANSI C99 [Azure IoT 中心 SDK](/azure/iot-hub/iot-hub-devguide-sdks) 使 IoT 应用程序能够在设备或后端运行。

- [Microsoft Graph 中的 OneDrive 和 SharePoint](https://dev.onedrive.com/README.htm)

  OneDrive API 提供了一组 HTTP 服务，用于将应用程序连接到 Office 365 和 SharePoint Server 2016 中的文件和文件夹。

## <a name="windows-and-cross-platform-networking-apis"></a>Windows 和跨平台网络 API

- [C++ REST SDK（代码名称“Casablanca”）](https://github.com/Microsoft/cpprestsdk)

  提供现代的跨平台异步 API，用于与 REST 服务进行交互。

  - 对任何 HTTP 服务器执行 REST 调用，内置有对 JSON 文档分析和序列化的支持
  - 支持 OAuth 1 和 2，包括本地重定向侦听器
  - 使 Websocket 连接到远程服务
  - 基于 PPL 的完全异步任务 API，包含内置线程池

  支持 Windows 桌面 (7+)、Windows Server (2012+)、通用 Windows 平台、Linux、OSX、Android 和 iOS。

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Windows 运行时 HTTP 客户端类在 .NET Framework 类上建模，后者在 System.Web 命名空间中具有相同的名称。 `HttpClient` 完全支持通过 HTTP 异步上载和下载，还完全支持可将自定义 HTTP 处理程序插入到管道中的管道筛选器。 Windows SDK 包括用于按流量计费的网络和 OAuth 身份验证等的样本筛选器。 对于仅面向通用 Windows 平台的应用，我们建议使用 `Windows::Web:HttpClient` 类。

- [IXMLHTTPRequest2 接口](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  提供可在 Windows 运行时应用或 Windows 桌面应用中使用的本机 COM 接口，用于通过 HTTP 连接到 Internet，并发布 GET、PUT 和其他 HTTP 命令。 有关详细信息，请参见[演练：使用任务和 XML HTTP 请求进行连接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  可以在 Windows 桌面应用中使用以连接到 Internet 的 Windows API。

## <a name="see-also"></a>请参阅

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Microsoft Azure C 和 C++ 开发人员中心](https://azure.microsoft.com/develop/cpp/) <br/>
[网络和 Web 服务 (UWP)](/windows/uwp/networking/)
