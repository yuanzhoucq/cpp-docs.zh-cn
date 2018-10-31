---
title: Windows 套接字类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 18537c0de09185c8cd219e3d17ef8bb297e1d711
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433600"
---
# <a name="windows-sockets-classes"></a>Windows 套接字类

Windows 套接字提供了一个在两台计算机之间进行通信的与网络协议无关的方法。 这些套接字可以是同步（你的程序等到通信完成才运行），也可以是异步的（你的程序在通信进行时继续运行）。

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
将 Windows 套接字封装在细包装器中。

[CSocket](../mfc/reference/csocket-class.md)<br/>
派生自 `CAsyncSocket` 的更高程度的抽象。 它同步运行。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
为 Windows 套接字提供 `CFile` 接口。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

