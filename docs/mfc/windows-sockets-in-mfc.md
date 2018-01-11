---
title: "MFC 中的 Windows 套接字 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdade770449b7ae5db9db9a170198b81cbeaf970
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows 套接字
> [!NOTE]
>  MFC 支持 Windows 套接字 1，但不支持[Windows 套接字 2](http://msdn.microsoft.com/library/windows/desktop/ms740673)。 首先，Windows 套接字 2 随 Windows 98，并是随 Windows 2000 附带的版本。  
  
 MFC 还提供有关编写 Windows 套接字，体现在两个 MFC 类使用的网络通信程序的两个模型。 本指南介绍了这些模型和更多详细信息 MFC 套接字支持。 "套接字"是一个终结点的通信： 通过该应用程序进行通信与其他 Windows 套接字应用程序在网络的对象。  
  
 有关 Windows 套接字，包括的套接字概念，说明信息请参阅[Windows 套接字： 背景](../mfc/windows-sockets-background.md)。  
  
##  <a name="_core_sockets_programming_models"></a>套接字编程模型  
 以下类支持两个 MFC Windows 套接字编程模型：  
  
-   `CAsyncSocket`  
  
     此类封装 Windows 套接字 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)是的程序员来说知道网络编程和需要一些编程直接与套接字 API 的灵活性，但还希望网络事件的通知的回调函数的便利性。 以外打包面向对象的形式以用于 c + + 中的套接字，此类提供的仅有的其他抽象将某些套接字相关的 Windows 消息转换为回调。 有关详细信息，请参阅[Windows 套接字： 套接字通知](../mfc/windows-sockets-socket-notifications.md)。  
  
-   `CSocket`  
  
     此类，派生自`CAsyncSocket`，提供用于处理通过 MFC 的套接字的更高级别抽象[CArchive](../mfc/reference/carchive-class.md)对象。 极大地与存档使用套接字类似于使用 MFC 的文件序列化协议。 这可以更容易地使用比`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)继承中的许多成员函数`CAsyncSocket`封装 Windows 套接字 Api; 你将需要使用其中的某些功能并了解套接字通常编程。 但是`CSocket`管理的需要自行使用原始 API 或类执行操作的通信的许多方面`CAsyncSocket`。 最重要的是，`CSocket`提供锁定 （于后台处理的 Windows 消息），这是至关重要的同步操作`CArchive`。  
  
 创建和使用`CSocket`和`CAsyncSocket`对象述[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows 套接字： 使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows 套接字 Dll  
 Microsoft Windows 操作系统提供的 Windows 套接字的动态链接库 (DLL)。 Visual c + + 提供了相应的标头文件、 库和 Windows 套接字规范。  
  
> [!NOTE]
>  在 Windows NT 和 Windows 2000，16 位应用程序的 Windows 套接字支持基于 WINSOCK。DLL。 对于 32 位应用程序，支持采用 WSOCK32。DLL。 提供的 Api 是相同，只不过 32 位版本具有加宽到 32 位的参数。 在 Win32 下，提供线程安全。  
  
 Windows 套接字有关的详细信息，请参阅：  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：操作顺序](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows 套接字：使用存档的套接字的示例](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows 套接字：使用存档的套接字如何工作](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：从套接字类派生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows 套接字：套接字通知](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows 套接字：阻止](../mfc/windows-sockets-blocking.md)  
  
-   [Windows 套接字：字节排序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows 套接字：转换字符串](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows 套接字：端口和套接字地址](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## <a name="see-also"></a>请参阅  
 [Windows 套接字](../mfc/windows-sockets.md)

