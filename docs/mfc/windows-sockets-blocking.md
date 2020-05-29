---
title: Windows 套接字：阻止
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359999"
---
# <a name="windows-sockets-blocking"></a>Windows 套接字：阻止

本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文包含锁定。 其他问题在文章中介绍[：Windows套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)和 Windows[套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或派生自类[CAsyncSocket，](../mfc/reference/casyncsocket-class.md)则需要自己管理这些问题。 如果您使用或派生自[CSocket](../mfc/reference/csocket-class.md)类，MFC 会为您管理它们。

## <a name="blocking"></a>阻塞

套接字可以处于“锁定模式”或“非锁定模式”。 处于锁定（或同步）模式的套接字的函数直到可完成其操作才会返回。 这称为“锁定”，因为调用其函数的套接字无法执行任何操作 - 在调用返回之前处于锁定状态。 例如，对成员`Receive`函数的调用可能需要任意很长时间才能完成，因为它等待发送应用程序发送（这是如果您正在使用`CSocket`或与阻塞一起使用）。 `CAsyncSocket` 如果`CAsyncSocket`对象处于非阻塞模式（异步操作），则调用会立即返回，并且当前错误代码（使用[GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror)成员函数可检索）为**WSAEANDBLOCK，** 指示如果调用由于该模式而没有立即返回，则该调用将被阻止。 （`CSocket`从不返回**WSAEE.BLOCK**。 此类为您管理锁定。）

套接字的行为在 32 位和 64 位操作系统下不同（如 Windows 95 或 Windows 98）于在 16 位操作系统下（如 Windows 3.1）。 不同于 16 位操作系统，32 位和 64 位操作系统使用强占式多任务并提供多线程处理。 在 32 位和 64 位操作系统下，您可在单独的辅助线程中放置套接字。 线程中的套接字可在不影响应用程序中其他活动的情况下锁定，并且锁定时不会占用计算机时间。 有关多线程编程的信息，请参阅文章["多线程"。](../parallel/multithreading-support-for-older-code-visual-cpp.md)

> [!NOTE]
> 在多线程应用程序中，您可以使用 `CSocket` 的锁定特性简化程序的设计，而不影响用户界面的响应能力。 通过在主线程处理用户交互并在备用线程中处理 `CSocket`，您可以分隔这些逻辑操作。 在不是多线程的应用程序中，这两个活动必须组合并作为单个线程处理，这通常意味着使用 `CAsyncSocket` 以便你可按需处理通信请求，或重写 `CSocket::OnMessagePending` 以在同步活动期间处理用户操作。

余下的讨论适用于面向 16 位操作系统的程序员：

通常，如果您使用的是 `CAsyncSocket`，则应避免使用锁定操作，应改用异步操作。 在异步操作中，从调用`Receive`后收到**WSAETOBLOCK**错误代码的点开始，例如，等待成员`OnReceive`函数调用以通知您可以再次读取。 异步调用是通过调用套接字的相应回调通知功能（如[OnReceive）](../mfc/reference/casyncsocket-class.md#onreceive)进行的。

在 Windows 下，锁定调用被视为不良实践。 默认情况下[，CAsyncSocket](../mfc/reference/casyncsocket-class.md)支持异步调用，您必须使用回调通知自行管理阻止。 另一方面[，CSocket](../mfc/reference/csocket-class.md)类是同步的。 它将为您推送 Windows 消息和管理锁定。

有关锁定的详细信息，请参阅 Windows 套接字规范。 有关"开"功能的详细信息，请参阅[Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)和[Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)。

有关详细信息，请参阅：

- [Windows 套接字：使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket：打开发送](../mfc/reference/casyncsocket-class.md#onsend)
