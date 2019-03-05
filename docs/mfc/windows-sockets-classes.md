---
title: Windows 套接字类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303815"
---
# <a name="windows-sockets-classes"></a>Windows 套接字类

Windows 套接字提供了一个在两台计算机之间进行通信的与网络协议无关的方法。 这些套接字可以是同步（您的程序等到通信完成才运行），也可以是异步的（您的程序在通信进行时继续运行）。

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
将 Windows 套接字封装在细包装器中。

[CSocket](../mfc/reference/csocket-class.md)<br/>
派生自 `CAsyncSocket` 的更高程度的抽象。 它同步运行。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
为 Windows 套接字提供 `CFile` 接口。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
