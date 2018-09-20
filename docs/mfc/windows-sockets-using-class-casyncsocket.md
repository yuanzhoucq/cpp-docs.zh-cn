---
title: Windows 套接字： 使用类 CAsyncSocket |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49e5df8e88124d1d94869618a94525e224d32495
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424660"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows 套接字：使用类 CAsyncSocket

本文介绍如何使用类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。 请注意，此类将封装 Windows 套接字 API 级别非常低。 `CAsyncSocket` 适用于由编程人员了解详细信息中的网络通信，但希望的网络事件通知的回调方便地使用。 基于此假设，这篇文章仅提供基本说明。 您可能应考虑使用`CAsyncSocket`如果希望 Windows 套接字的易用性与 MFC 应用程序中的多个网络协议的处理，但不是想要以牺牲灵活性为代价。 你还可能会觉得您可以通过编程的更多的通信，直接自行比你无法使用类的更一般的替代模型获取更高的效率`CSocket`。

`CAsyncSocket` 中所述*MFC 参考*。 Visual c + + 还提供 Windows 套接字规范，位于 Windows SDK 中。 细节被留给您。 Visual c + + 未提供的示例应用程序`CAsyncSocket`。

如果您不了高度掌握网络通信，需要一个简单的解决方案，使用类[CSocket](../mfc/reference/csocket-class.md)与`CArchive`对象。 请参阅[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)有关详细信息。

本文包含以下内容：

- 创建和使用`CAsyncSocket`对象。

- [您的职责与 CAsyncSocket](#_core_your_responsibilities_with_casyncsocket)。

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> 创建和使用 CAsyncSocket 对象

#### <a name="to-use-casyncsocket"></a>若要使用 CAsyncSocket

1. 构造[CAsyncSocket](../mfc/reference/casyncsocket-class.md)对象，并使用该对象创建基础**套接字**处理。

     套接字的创建遵循两阶段构造的 MFC 模式。

     例如：

     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     或

     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

     上面的第一个构造函数创建`CAsyncSocket`在堆栈上的对象。 第二个构造函数创建`CAsyncSocket`堆上。 第一个[创建](../mfc/reference/casyncsocket-class.md#create)调用上面使用的默认参数来创建流套接字。 第二个`Create`调用使用指定的端口和地址创建一个数据报套接字。 (你可以使用`Create`采用哪种构造方法的版本。)

     为参数`Create`是：

   - "端口": 短整数。

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - 套接字类型： **SOCK_STREAM** （默认值） 或**SOCK_DGRAM**。

   - 一个套接字"地址"，如"ftp.microsoft.com"或"128.56.22.8"。

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

     中所述的条款"端口"和"套接字地址" [Windows 套接字： 端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)。

1. 如果套接字，客户端套接字对象连接到服务器套接字，使用[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)。

     或

     如果套接字是服务器，设置要开始侦听的套接字 (与[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) 从客户端的连接尝试。 收到连接请求后，它具有接受[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)。

     接受连接，可以执行此类验证密码的任务。

    > [!NOTE]
    >  `Accept`成员函数将一个新的空引用`CSocket`对象作为其参数。 在调用之前，必须构造此对象`Accept`。 如果此套接字对象超出范围，则关闭连接。 不要调用`Create`此新的套接字对象。 有关示例，请参阅文章[Windows 套接字： 操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

1. 通过调用执行与其他套接字通信`CAsyncSocket`封装 Windows 套接字 API 函数的对象的成员函数。

     请参阅 Windows 套接字规范和类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)中*MFC 参考*。

1. 销毁`CAsyncSocket`对象。

     如果在堆栈上创建的套接字对象，包含函数超出范围时调用其析构函数。 如果在堆上创建的套接字对象，使用**新**运算符，您应负责使用**删除**运算符来销毁该对象。

     析构函数调用的对象[关闭](../mfc/reference/casyncsocket-class.md#close)之前销毁的对象的成员函数。

有关此序列中的代码示例 (实际上为`CSocket`对象)，请参阅[Windows 套接字： 操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> 您的职责与 CAsyncSocket

创建类的对象时[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，该对象封装 Windows**套接字**句柄并提供对该句柄的操作。 当你使用`CAsyncSocket`，必须处理可能会遇到如果直接使用 API 的所有问题。 例如：

- "阻止"方案。

- 在发送和接收计算机之间的字节顺序差异。

- Unicode 和多字节字符之间进行转换设置 (MBCS) 字符串。

术语的定义这些以及其他信息，请参阅[Windows 套接字： 阻止](../mfc/windows-sockets-blocking.md)， [Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)， [Windows 套接字： 转换字符串](../mfc/windows-sockets-converting-strings.md).

尽管这些问题，类`CAsycnSocket`可能是正确的选择，如果应用程序需要的所有灵活性和控制可以获取。 如果不是，你应考虑使用类`CSocket`相反。 `CSocket` 隐藏从你的详细信息： 泵 Windows 期间阻止调用消息，并为您提供了访问权限的 it `CArchive`，用于管理的字节顺序差异并为您的字符串转换。

有关详细信息，请参见:

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

