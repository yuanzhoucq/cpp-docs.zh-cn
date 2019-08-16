---
title: MFC 中的 Windows 套接字
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 44a4838a1cd863bd484701966a156be9f61f8988
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510627"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows 套接字

> [!NOTE]
>  MFC 支持 Windows 套接字 1, 但不支持[Windows 套接 2](/windows/win32/WinSock/windows-sockets-start-page-2)。 Windows 套接字2首次随附于 Windows 98, 是 Windows 2000 随附的版本。

MFC 提供了两个模型用于写入包含在两个 MFC 类中的 Windows 套接字的网络通信程序。 本文介绍了这些模型以及 MFC 套接字支持的详细信息。 "套接字" 是通信终结点: 一个对象, 应用程序通过该对象与网络中的其他 Windows 套接字应用程序进行通信。

有关 windows 套接字的信息, 包括套接字概念的说明, 请[参阅 windows 套接字:背景](../mfc/windows-sockets-background.md)。

##  <a name="_core_sockets_programming_models"></a>套接字编程模型

以下类支持两个 MFC Windows 套接字编程模型:

- `CAsyncSocket`

   此类封装 Windows 套接字 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)适用于了解网络编程的程序员, 并希望灵活地直接编程到套接字 API, 但也希望回调函数为网络事件通知提供便利。 此类提供的其他唯一抽象是将特定于套C++接字相关的 Windows 消息转换为回调, 而不是以面向对象的形式打包套接字。 有关详细信息, 请[参阅 Windows 套接字:套接字](../mfc/windows-sockets-socket-notifications.md)通知。

- `CSocket`

   此类派生自`CAsyncSocket`, 它提供了更高级别的抽象, 可通过 MFC [CArchive](../mfc/reference/carchive-class.md)对象处理套接字。 将套接字与存档结合使用非常类似于使用 MFC 的文件序列化协议。 这样就可以更轻松地使用`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)继承`CAsyncSocket`了多个封装 Windows 套接字 api 的成员函数; 您必须使用其中一些功能, 并且通常需要了解套接字编程。 但`CSocket`通过使用原始 API 或类`CAsyncSocket`, 管理通信的许多方面。 最重要的`CSocket`是, 提供阻止 (对 Windows 消息进行后台处理), 这对的同步`CArchive`操作非常重要。

Windows 套接字`CSocket`中`CAsyncSocket` [介绍了如何创建和使用和对象:将套接字用于](../mfc/windows-sockets-using-sockets-with-archives.md)存档[和 Windows 套接字:使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows 套接字 Dll

Microsoft Windows 操作系统提供 Windows 套接字动态链接库 (DLL)。 视觉C++对象提供适当的标头文件和库和 Windows 套接字规范。

有关 Windows 套接字的详细信息, 请参阅:

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

- [Windows 套接字：结合使用套接字和存档](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows 套接字：使用存档的套接字示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows 套接字：使用存档的套接字的工作原理](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)

- [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)

- [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)

- [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)

- [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>请参阅

[Windows 套接字](../mfc/windows-sockets.md)
