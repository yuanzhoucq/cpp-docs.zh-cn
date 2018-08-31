---
title: MFC 中的 Windows 套接字 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8b497fc7e5e22a654d1f5037a983165fcd5594c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194976"
---
# <a name="windows-sockets-in-mfc"></a>MFC 中的 Windows 套接字
> [!NOTE]
>  MFC 支持 Windows 套接字 1，但不支持[Windows 套接字 2](/windows/desktop/WinSock/windows-sockets-start-page-2)。 Windows 套接字 2 首次随 Windows 98，是 Windows 2000 中包含的版本。  
  
 MFC 提供两种用于编写与 Windows 套接字，体现在两个 MFC 类的网络通信程序模型。 本文介绍了这些模型，以及更多详细信息 MFC 套接字支持。 一个"套接字"是通信的终结点： 通过该应用程序进行通信与其他 Windows 套接字应用程序在网络上的对象。  
  
 了解 Windows 套接字，包括套接字概念的说明请参阅[Windows 套接字： 背景](../mfc/windows-sockets-background.md)。  
  
##  <a name="_core_sockets_programming_models"></a> 套接字编程模型  
 以下类支持两个 MFC Windows 套接字编程模型：  
  
-   `CAsyncSocket`  
  
     此类封装 Windows 套接字 API。 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)是编程人员了解网络编程并且想直接针对套接字 API 编程的灵活性，但还希望的网络事件通知的回调函数的便利性。 非打包面向对象的 c + + 中使用的窗体中的套接字，此类提供的唯一附加抽象转换为某些与套接字相关的 Windows 消息的回调。 有关详细信息，请参阅[Windows 套接字： 套接字通知](../mfc/windows-sockets-socket-notifications.md)。  
  
-   `CSocket`  
  
     此类派生自`CAsyncSocket`，提供用于处理通过 MFC 套接字的更高级别抽象[CArchive](../mfc/reference/carchive-class.md)对象。 极大地与存档使用套接字类似于使用 MFC 的文件的序列化协议。 这可以更容易地使用比`CAsyncSocket`模型。 [CSocket](../mfc/reference/csocket-class.md)继承许多成员函数从`CAsyncSocket`，它封装 Windows 套接字 Api; 你将需要使用其中的一些功能和了解套接字编程通常。 但是`CSocket`管理的通信时可能需要自行使用原始 API 或类进行很多方面`CAsyncSocket`。 最重要的是，`CSocket`提供锁定 （与后台处理的 Windows 消息），这是至关重要的同步操作`CArchive`。  
  
 创建和使用`CSocket`并`CAsyncSocket`对象中所述[Windows 套接字： 使用存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)并[Windows 套接字： 使用类 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)。  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows 套接字 Dll  
 Microsoft Windows 操作系统提供的 Windows 套接字的动态链接库 (DLL)。 Visual c + + 提供了相应的标头文件、 库和 Windows 套接字规范。  
  
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

