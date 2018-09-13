---
title: Win32 Internet 类 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.win32
dev_langs:
- C++
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1e93c2c3ea9efeb8be6ec5d79b9f2ef7729b9e9
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534932"
---
# <a name="win32-internet-classes"></a>Win32 Internet 类
MFC 包装 Win32 Internet (WinInet) 和 ActiveX 技术，以使 Internet 编程更简单。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。
  
  
 [CInternetSession](../mfc/reference/cinternetsession-class.md)  
 创建和初始化一个 Internet 会话或多个同时 Internet 会话，并如有必要，描述向代理服务器连接。  
  
 [CInternetConnection](../mfc/reference/cinternetconnection-class.md)  
 管理与 Internet 服务器的连接。  
  
 [CInternetFile](../mfc/reference/cinternetfile-class.md)  
 此类和其派生的类允许对使用 Internet 协议的远程系统上的文件的访问。  
  
 [CHttpConnection](../mfc/reference/chttpconnection-class.md)  
 管理与 HTTP 服务器的连接。  
  
 [CHttpFile](../mfc/reference/chttpfile-class.md)  
 提供的功能来查找和读取 HTTP 服务器上的文件。  
  
 [CGopherFile](../mfc/reference/cgopherfile-class.md)  
 提供查找和读取 Gopher 服务器上文件的功能。  
  
 [CFtpConnection](../mfc/reference/cftpconnection-class.md)  
 管理与 FTP 服务器的连接。  
  
 [CGopherConnection](../mfc/reference/cgopherconnection-class.md)  
 管理与 gopher 服务器的连接。  
  
 [CFileFind](../mfc/reference/cfilefind-class.md)  
 执行本地和 Internet 文件搜索。  
  
 [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)  
 辅助 FTP 服务器的 Internet 文件搜索。  
  
 [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)  
 辅助 Gopher 服务器的 Internet 文件搜索。  
  
 [CGopherLocator](../mfc/reference/cgopherlocator-class.md)  
 从 Gopher 服务器获取 Gopher“定位器”，确定定位器的类型，并使定位器可用于 `CGopherFileFind`。  
  
 [CInternetException](../mfc/reference/cinternetexception-class.md)  
 表示与 Internet 操作相关的异常条件。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

