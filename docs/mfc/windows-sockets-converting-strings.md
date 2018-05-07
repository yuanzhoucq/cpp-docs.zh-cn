---
title: Windows 套接字： 转换字符串 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad57be68ce716cddf2ce44f12e94c545a7bbfd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-converting-strings"></a>Windows 套接字：转换字符串
本文和两篇配套文章介绍了 Windows 套接字编程中的若干问题。 本文介绍如何将字符串转换。 中涉及的其他问题[Windows 套接字： 阻止](../mfc/windows-sockets-blocking.md)和[Windows 套接字： 字节排序](../mfc/windows-sockets-byte-ordering.md)。  
  
 如果你使用或派生自类[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，你将需要管理这些问题。 如果你使用或派生自类[CSocket](../mfc/reference/csocket-class.md)，MFC 将为你管理这些问题。  
  
## <a name="converting-strings"></a>将字符串转换  
 如果您使用存储在不同的宽字符格式的字符串，如 Unicode 或多字节字符设置 (MBCS) 的应用程序之间进行通信或其中一种，使用 ANSI 字符字符串的应用程序，你必须管理转换自行下`CAsyncSocket`。 `CArchive`与使用对象`CSocket`对象管理此转换为你通过功能的类[CString](../atl-mfc-shared/reference/cstringt-class.md)。 有关详细信息，请参阅 Windows 套接字规范，位于 Windows SDK 中。  
  
 有关详细信息，请参见:  
  
-   [Windows 套接字：使用 CAsyncSocket 类](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows 套接字：对存档使用套接字](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows 套接字：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows 套接字：流套接字](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows 套接字：数据报套接字](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)

