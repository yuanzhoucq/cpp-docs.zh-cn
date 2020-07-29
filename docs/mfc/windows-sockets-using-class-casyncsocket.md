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
ms.openlocfilehash: 6a3b3469b908eaf6f8062b8db7fc4287606b7f02
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228500"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows 套接字：使用类 CAsyncSocket

本文介绍如何使用类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。 请注意，此类在很低的级别封装 Windows 套接字 API。 `CAsyncSocket`适用于了解网络通信的程序员的使用，但希望为网络事件通知提供回调的便利。 根据此假设，本文仅提供基本说明。 `CAsyncSocket`如果希望 Windows 套接字在 MFC 应用程序中轻松处理多个网络协议，但不希望牺牲灵活性，则可以考虑使用。 你可能还会发现，你可以通过直接对通信编程，而不是使用类的更常规备选模型，来提高效率 `CSocket` 。

`CAsyncSocket`在*MFC 参考*中进行了介绍。 Visual C++ 还提供 Windows SDK 中的 Windows 套接字规范。 详细信息留给你。 Visual C++ 不提供的示例应用程序 `CAsyncSocket` 。

如果你不了解网络通信并想要使用简单的解决方案，请对对象[CSocket](../mfc/reference/csocket-class.md)使用类 CSocket `CArchive` 。 有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)。

本文介绍：

- 创建和使用 `CAsyncSocket` 对象。

- [你的 CAsyncSocket 责任](#_core_your_responsibilities_with_casyncsocket)。

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>创建和使用 CAsyncSocket 对象

#### <a name="to-use-casyncsocket"></a>使用 CAsyncSocket

1. 构造一个[CAsyncSocket](../mfc/reference/casyncsocket-class.md)对象，并使用对象创建基础**套接字句**柄。

   套接字的创建遵循两阶段构造的 MFC 模式。

   例如：

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     \- 或 -

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上面的第一个构造函数 `CAsyncSocket` 在堆栈上创建对象。 第二个构造函数 `CAsyncSocket` 在堆上创建一个。 上面的第一个[Create](../mfc/reference/casyncsocket-class.md#create)调用使用默认参数创建流套接字。 第二个 `Create` 调用使用指定的端口和地址创建数据报套接字。 （可将任一 `Create` 版本用于任一构造方法。）

   的参数为 `Create` ：

   - "端口"：短整数。

      对于服务器套接字，必须指定端口。 对于客户端套接字，通常接受此参数的默认值，这会使 Windows 套接字选择端口。

   - 套接字类型： **SOCK_STREAM** （默认值）或**SOCK_DGRAM**。

   - 套接字 "address"，如 "ftp.microsoft.com" 或 "128.56.22.8"。

      这是网络上的 Internet 协议（IP）地址。 你可能始终会依赖于此参数的默认值。

   [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)中介绍了术语 "端口" 和 "套接字地址"。

1. 如果套接字是客户端，请使用[CAsyncSocket：： connect](../mfc/reference/casyncsocket-class.md#connect)将套接字对象连接到服务器套接字。

     -或-

   如果套接字是服务器，请将套接字设置为开始侦听（使用[CAsyncSocket：：侦听](../mfc/reference/casyncsocket-class.md#listen)），以便从客户端进行连接尝试。 收到连接请求后，请使用[CAsyncSocket：： accept](../mfc/reference/casyncsocket-class.md#accept)接受它。

   接受连接后，您可以执行类似验证密码的任务。

    > [!NOTE]
    >  `Accept`成员函数使用新的空 `CSocket` 对象作为其参数。 在调用之前，必须构造此对象 `Accept` 。 如果此套接字对象超出范围，则关闭连接。 不要 `Create` 为此新的套接字对象调用。 有关示例，请参阅[Windows 套接字：操作序列一](../mfc/windows-sockets-sequence-of-operations.md)文。

1. 通过调用 `CAsyncSocket` 封装 Windows 套接字 API 函数的对象的成员函数，执行与其他套接字的通信。

   请参阅*MFC 参考*中的 Windows 套接字规范和类[CAsyncSocket](../mfc/reference/casyncsocket-class.md) 。

1. 销毁 `CAsyncSocket` 对象。

   如果在堆栈上创建了套接字对象，则在包含函数超出范围时将调用其析构函数。 如果使用运算符在堆上创建套接字对象 **`new`** ，则需要负责使用 **`delete`** 运算符销毁对象。

   析构函数在销毁对象之前调用对象的[关闭](../mfc/reference/casyncsocket-class.md#close)成员函数。

有关代码中的此序列的示例（实际上适用于 `CSocket` 对象），请参阅[Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)。

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>你的 CAsyncSocket 责任

当你创建[CAsyncSocket](../mfc/reference/casyncsocket-class.md)类的对象时，对象将封装一个 Windows**套接字**句柄并在该句柄上提供操作。 当你使用时 `CAsyncSocket` ，如果直接使用 API，则必须处理你可能遇到的所有问题。 例如：

- "阻止" 方案。

- 发送计算机和接收计算机之间的字节顺序差异。

- 在 Unicode 和多字节字符集（MBCS）字符串之间进行转换。

有关这些条款和其他信息的定义，请参阅[Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)， [windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)， [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)。

尽管存在这些问题， `CAsycnSocket` 但如果您的应用程序需要可以获得的所有灵活性和控制，则类可能是正确的选择。 否则，应考虑 `CSocket` 改用类。 `CSocket`从你中隐藏了很多详细信息：它在阻止调用期间抽取 Windows 消息，并提供对的访问权限 `CArchive` ，从而管理字节顺序差异和字符串转换。

有关详细信息，请参阅：

- [Windows 套接字：背景](../mfc/windows-sockets-background.md)

- [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)

- [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)
