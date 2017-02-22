---
title: "CSocketFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archives [C++], 网络"
  - "CSocketFile class"
  - "networks [C++], archive"
  - "networks [C++], serializing to"
  - "序列化 [C++], 网络"
  - "SOCKET handle"
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CSocketFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于发送和接收在网络中使用的数据的 `CFile` 对象通过Windows套接字。  
  
## 语法  
  
```  
class CSocketFile : public CFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSocketFile::CSocketFile](../Topic/CSocketFile::CSocketFile.md)|构造 `CSocketFile` 对象。|  
  
## 备注  
 可以为此附加到 `CSocket` 对象的 `CSocketFile` 对象。  您还可以为和通常，附加到 `CArchive` 对象的 `CSocketFile` 对象简化发送和接收数据使用MFC序列化。  
  
 序列化（发送）数据，将其插入到存档中，调用 `CSocketFile` 成员函数以将数据写入 `CSocket` 对象。  若要反序列化（接收）数据，则从存档提取。  这会导致存档调用 `CSocketFile` 成员函数读取 `CSocket` 对象的数据。  
  
> [!TIP]
>  除了使用 `CSocketFile` 外如下所述，可以将其用作独立文件对象，就象可以使用 `CFile`，其基类。  还可以用于任何基于存档的MFC序列化功能的 `CSocketFile`。  由于 `CSocketFile` 不支持所有`CFile`的功能，某些默认MFC序列化功能与 `CSocketFile`兼容。  这是尤其如此 `CEditView` 选件类。  不应尝试使用 `CEditView::SerializeRaw`附加到 `CSocketFile` 对象的 `CArchive` 对象序列化 `CEditView` 数据;使用 **CEditView::Serialize**。  `SerializeRaw` 函数需要文件对象具有功能，例如 `Seek`，`CSocketFile` 没有。  
  
 当您使用 `CArchive` 和 `CSocketFile` 和 `CSocket`时，可能会遇到 **CSocket::Receive** 输入循环的情况\( **PumpMessages\(FD\_READ\)**\)等待请求的少量字节。  这是因为，Windows套接字只允许一recv每个FD\_READ通知调用，但是，`CSocketFile` 和 `CSocket` 允许多个recv每FD\_READ调用。  如果收到FD\_READ，而没有读取数据，应用程序停止。  如果不会收到另一个FD\_READ，应用程序停止间通信套接字。  
  
 通过以下方式可以解决此问题。  在您的套接字选件类 `OnReceive` 方法，请调用 **CAsyncSocket::IOCtl\(FIONREAD, ...\)**，在调用您的邮件类之前 `Serialize` 方法，当从套接字要读取的所需的数据超过一TCP数据包时\(中等的网络，通常至少1096个字节的最大传输单位的范围）。  如果可用数据的大小程度低于必要，等待所有数据接收和此时开始这次读取操作。  
  
 在下面的示例中，`m_dwExpected` 是用户所需接收的近似字节数。  假定，可以在代码中的其他位置声明它。  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/CPP/csocketfile-class_1.cpp)]  
  
 有关更多信息，请参见 [在MFC的Windows套接字](../../mfc/windows-sockets-in-mfc.md)、 [Windows套接字:使用套接字与存档](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及 [Windows套接字2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## 要求  
 **Header:** afxsock.h  
  
## 请参阅  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)