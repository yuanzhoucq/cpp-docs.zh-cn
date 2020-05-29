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
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371099"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows 套接字

> [!NOTE]
> MFC 支持 Windows 套接字 1，但不支持[Windows 套接字 2](/windows/win32/WinSock/windows-sockets-start-page-2)。 Windows 套接字 2 首次随 Windows 98 一起提供，是 Windows 2000 附带的版本。

MFC 提供两种模型，用于使用 Windows 套接字编写网络通信程序，这体现在两个 MFC 类中。 本文介绍了这些模型，以及 MFC 套接字支持的进一步详细信息。 "套接字"是通信的终结点：应用程序通过网络与其他 Windows 套接字应用程序通信的对象。

有关 Windows 套接字的信息（包括套接字概念的说明），请参阅[Windows 套接字：背景](../mfc/windows-sockets-background.md)。

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>套接字编程模型

以下类支持两种 MFC Windows 套接字编程模型：

- `CAsyncSocket`

   此类封装 Windows 套接字 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)适用于了解网络编程并希望编程灵活性直接到套接字 API 的程序员，但也希望回调函数的便利性用于通知网络事件。 除了以面向对象的形式打包套接字以用于C++外，此类提供的唯一附加抽象是将某些与套接字相关的 Windows 消息转换为回调。 有关详细信息，请参阅[Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)。

- `CSocket`

   此类派生自`CAsyncSocket`，提供更高级别的抽象，用于通过 MFC [CArchive](../mfc/reference/carchive-class.md)对象处理套接字。 使用具有存档的套接字与使用 MFC 的文件序列化协议非常相似。 这使得它比`CAsyncSocket`模型更易于使用。 [CSocket](../mfc/reference/csocket-class.md)从`CAsyncSocket`封装 Windows 套接字 API 继承了许多成员函数;您必须使用其中一些函数，并了解套接字编程。 但是`CSocket`管理通信的许多方面，您必须自己使用原始 API 或类`CAsyncSocket`。 最重要的是，`CSocket`提供阻塞（对 Windows 消息进行后台处理），这对于`CArchive`的同步操作至关重要。

创建和使用`CSocket`和`CAsyncSocket`对象在[Windows 套接字中描述：使用包含存档](../mfc/windows-sockets-using-sockets-with-archives.md)和 Windows[套接字的套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows 套接字 DLL

微软 Windows 操作系统提供 Windows 套接字动态链接库 （DLL）。 可视C++提供相应的标头文件和库以及 Windows 套接字规范。

有关 Windows 套接字的详细信息，请参阅：

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)

- [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)

- [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)

- [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)

- [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>另请参阅

[窗口套接字](../mfc/windows-sockets.md)
