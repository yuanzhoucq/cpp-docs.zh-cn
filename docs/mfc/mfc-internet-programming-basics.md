---
title: MFC Internet 编程基础知识
ms.date: 11/19/2018
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366292"
---
# <a name="mfc-internet-programming-basics"></a>MFC Internet 编程基础知识

Microsoft 提供了许多 API 来编程客户端和服务器应用程序。 许多新应用程序正在为 Internet 编写，随着技术、浏览器功能和安全选项的变化，将编写新型应用程序。 浏览器在客户端计算机上运行，提供对万维网的访问，并显示包含文本、图形、ActiveX 控件和文档的 HTML 页面。 服务器提供 FTP、HTTP 和 gopher 服务，并使用 CGI 运行服务器扩展应用程序。 自定义应用程序可以检索信息并在 Internet 上提供数据。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

![客户端和服务器应用程序](../mfc/media/vc38bq1.gif "客户端和服务器应用程序")

MFC 提供支持 Internet 编程的类。 您可以使用[COleControl](../mfc/reference/colecontrol-class.md)和[CDocObjectServer](../mfc/reference/cdocobjectserver-class.md)以及相关的 MFC 类来编写 ActiveX 控件和活动文档。 您可以使用 MFC 类（如[CInternetSession、CFtpConnect](../mfc/reference/cftpconnection-class.md)和[CAsyncMonikerFile）](../mfc/reference/casyncmonikerfile-class.md)使用 Internet 协议（如 FTP、HTTP 和 gopher）检索文件和信息。 [CInternetSession](../mfc/reference/cinternetsession-class.md)

## <a name="in-this-section"></a>本节内容

- [互联网相关 MFC 类](../mfc/internet-related-mfc-classes.md)

- [按主题发布的互联网信息](../mfc/internet-information-by-topic.md)

- [按任务进行互联网信息](../mfc/internet-information-by-task.md)

- [互联网上的主动技术](../mfc/active-technology-on-the-internet.md)

- [温尼特基础知识](../mfc/wininet-basics.md)

- [HTML 基础知识](../mfc/html-basics.md)

## <a name="related-sections"></a>相关章节

- [互联网上的 ActiveX 控制](../mfc/activex-controls-on-the-internet.md)

- [互联网上的异步月客](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32 互联网扩展（WinInet）](../mfc/win32-internet-extensions-wininet.md)

- [MFC 互联网编程任务](../mfc/mfc-internet-programming-tasks.md)

- [应用程序设计选择](../mfc/application-design-choices.md)

- [编写 MFC 应用程序](../mfc/writing-mfc-applications.md)

- [测试互联网应用](../mfc/testing-internet-applications.md)

- [互联网安全](../mfc/internet-security-cpp.md)

- [ATL 支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>网站了解更多信息

有关 Microsoft 互联网技术的其他信息，请参阅[Microsoft 开发人员网络 （MSDN）](https://go.microsoft.com/fwlink/p/?linkid=56322)网站。 （链接可能会更改，恕不另行通知。

此开发人员网站包含有关使用 Microsoft 开发工具和技术的信息，以及有关最近和即将举办的会议的头条新闻。 从此页面中，您可以跳转到许多相关的开发人员网站，包括 .NET 和 XML 开发人员中心。 您还可以下载测试版 SDK 和示例。

[万维网联盟 （W3C）](https://go.microsoft.com/fwlink/p/?linkid=37125)发布 HTML、HTTP、CGI 和其他万维网技术的规范。

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>更多互联网帮助

Windows SDK 的 OLE 部分包含有关 OLE 编程的其他信息。 此信息提供有关直接使用 Win32 WinInet 函数的详细信息，而不是通过 MFC 类。 它还包含有关互联网技术的概述信息。
