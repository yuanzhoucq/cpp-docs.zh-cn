---
title: Windows 套接字：使用类 CAsyncSocket
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371971"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows 套接字：使用类 CAsyncSocket

本文介绍如何使用类[CAsyncSocket。](../mfc/reference/casyncsocket-class.md) 请注意，此类在非常低的级别封装 Windows 套接字 API。 `CAsyncSocket`供程序员使用，他们详细了解网络通信，但希望回拨的便利性用于通知网络事件。 基于此假设，本文仅提供基本说明。 如果您希望 Windows 套`CAsyncSocket`接字在 MFC 应用程序中轻松处理多个网络协议，但不想牺牲灵活性，则可能需要考虑使用。 您可能还觉得，通过更直接地编程通信，您比使用更通用的类`CSocket`替代模型更直接地编程，可以获得更好的效率。

`CAsyncSocket`记录在*MFC 参考*中。 可视C++还提供位于 Windows SDK 中的 Windows 套接字规范。 详情将留给你。 可视C++不提供`CAsyncSocket`的示例应用程序。

如果您对网络通信了解不够，并且想要一个简单的解决方案，请使用类[CSocket](../mfc/reference/csocket-class.md)与`CArchive`对象。 有关详细信息[，请参阅 Windows 套接字：使用带存档的套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。

本文介绍：

- 创建和使用`CAsyncSocket`对象。

- [您在 CAsyncSocket 中的职责](#_core_your_responsibilities_with_casyncsocket)。

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>创建和使用 CAsyncSocket 对象

#### <a name="to-use-casyncsocket"></a>使用 CAsyncSocket

1. 构造一个[CAsyncSocket](../mfc/reference/casyncsocket-class.md)对象，并使用 该对象创建基础**SOCKET**句柄。

   套接字的创建遵循两阶段构造的 MFC 模式。

   例如：

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -或-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上面的第一个构造函数在`CAsyncSocket`堆栈上创建一个对象。 第二个构造函数在`CAsyncSocket`堆上创建 一个。 上面的第一个[创建](../mfc/reference/casyncsocket-class.md#create)调用使用默认参数创建流套接字。 第二`Create`个调用创建具有指定端口和地址的数据报号套接字。 （您可以将任一`Create`版本与任一构造方法一起使用。

   要的`Create`参数是：

   - "端口"：短整数。

      对于服务器套接字，必须指定端口。 对于客户端套接字，您通常接受此参数的默认值，该值允许 Windows 套接字选择端口。

   - 套接字类型 **：SOCK_STREAM（** 默认值）或**SOCK_DGRAM。**

   - 套接字"地址"，如"ftp.microsoft.com"或"128.56.22.8"。

      这是您的互联网协议 （IP） 地址。 您可能始终依赖于此参数的默认值。

   术语"端口"和"套接字地址"在[Windows 套接字：端口和套接字地址）](../mfc/windows-sockets-ports-and-socket-addresses.md)中解释。

1. 如果套接字是客户端，请使用[CAsyncSocket：：连接](../mfc/reference/casyncsocket-class.md#connect)将套接字对象连接到服务器套接字：连接 。

     -或-

   如果套接字是服务器，请将套接字设置为开始侦听（使用[CAsyncSocket：：LISTEN），](../mfc/reference/casyncsocket-class.md#listen)以便从客户端进行连接尝试。 收到连接请求后，请使用[CAsyncSocket 接受：接受](../mfc/reference/casyncsocket-class.md#accept)。

   接受连接后，可以执行验证密码等任务。

    > [!NOTE]
    >  成员`Accept`函数以引用新的空`CSocket`对象作为其参数。 在调用`Accept`之前，必须构造此对象。 如果此套接字对象超出范围，则关闭连接。 不要调用`Create`此新套接字对象。 例如，请参阅文章 Windows[套接字：操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

1. 通过调用封装 Windows 套接字`CAsyncSocket`API 函数的对象成员函数，与其他套接字执行通信。

   请参阅*MFC 参考*中的 Windows 套接字规范和类[CAsyncSocket。](../mfc/reference/casyncsocket-class.md)

1. 销毁`CAsyncSocket`对象。

   如果在堆栈上创建了套接字对象，则当包含函数超出范围时，将调用其析构函数。 如果在堆上创建了套接字对象，请使用**新**运算符，则负责使用**delete**运算符销毁该对象。

   析构函数在销毁对象之前调用对象的[Close](../mfc/reference/casyncsocket-class.md#close)成员函数。

有关代码中此序列的示例（实际上对于`CSocket`对象），请参阅 Windows[套接字：操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>您对 CAsyncSocket 的责任

创建类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)的对象时，该对象封装 Windows **SOCKET**句柄，并为此句柄提供操作。 使用`CAsyncSocket`时，必须处理直接使用 API 时可能面临的所有问题。 例如：

- "阻止"方案。

- 发送和接收计算机之间的字节订单差异。

- 在 Unicode 和多字节字符集 （MBCS） 字符串之间进行转换。

有关这些条款的定义和其他信息，请参阅[Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)[、Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)[、Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)。

尽管存在这些问题，如果应用程序`CAsycnSocket`需要您可以获得的所有灵活性和控制，类可能是您的最佳选择。 如果没有，则应考虑改用类`CSocket`。 `CSocket`隐藏了很多细节：它在阻止调用期间泵送 Windows 消息，并允许您访问`CArchive`，该消息为您管理字节顺序差异和字符串转换。

有关详细信息，请参阅：

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
