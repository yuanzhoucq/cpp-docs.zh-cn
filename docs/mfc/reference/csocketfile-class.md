---
title: "CSocketFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- networks [C++], archive
- serialization [C++], network
- networks [C++], serializing to
- CSocketFile class
- archives [C++], network
- SOCKET handle
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 6ca331c07e0a9fc48f152042fcccd5c38e743ccf
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="csocketfile-class"></a>CSocketFile 类
用于通过 Windows 套接字在网络中发送和接收数据的 `CFile` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|构造 `CSocketFile` 对象。|  
  
## <a name="remarks"></a>备注  
 您可以将附加`CSocketFile`对象传递给`CSocket`实现此目的的对象。 也可以，并通常，附加`CSocketFile`对象传递给`CArchive`对象来简化了发送和接收使用 MFC 序列化数据。  
  
 要序列化 （发送） 数据，应将其插入到存档，其中调用`CSocketFile`成员函数以将数据写入到`CSocket`对象。 要反序列化 （接收） 存档中提取数据。 这将导致要调用的存档`CSocketFile`成员函数从中读取数据`CSocket`对象。  
  
> [!TIP]
>  除了使用`CSocketFile`如下所述，您可以使用它作为独立的文件对象，就像可以使用`CFile`，将其基类。 您还可以使用`CSocketFile`与任何基于存档的 MFC 序列化函数。 因为`CSocketFile`不支持所有的`CFile`的功能，某些默认 MFC 序列化函数中不符合`CSocketFile`。 更是如此的`CEditView`类。 不应尝试序列化`CEditView`通过数据`CArchive`对象附加到`CSocketFile`对象使用`CEditView::SerializeRaw`; 使用**CEditView::Serialize**相反。 `SerializeRaw`函数需要使用文件对象可以具有的功能，如`Seek`，则该`CSocketFile`没有。  
  
 当您使用`CArchive`与`CSocketFile`和`CSocket`，可能会遇到的情况其中**CSocket::Receive**进入一个循环 (通过**PumpMessages(FD_READ)**) 等待请求的字节量。 这是因为 Windows 套接字让每个 FD_READ 通知只有一个接收调用，但`CSocketFile`和`CSocket`允许每个 FD_READ 的多个接收调用。 如果没有要读取的数据时获取 FD_READ，请将挂起该应用程序。 如果您永远不会收到另一台 FD_READ，该应用程序将停止通过套接字进行通信。  
  
 您可以解决此问题，如下所示。 在`OnReceive`您套接字类方法，调用**CAsyncSocket::IOCtl (FIONREAD，...)**之前调用`Serialize`消息类时所需的数据等待从套接字读取超过一个 TCP 数据包 （最大传输单位的网络中，通常至少 1096 字节） 的大小的方法。 如果在可用数据的大小小于所需，等待要接收和只有此时才开始读取的操作的所有数据。  
  
 在下面的示例中，`m_dwExpected`是近似的用户期望接收的字节数。 假定，您将其声明在其他地方在代码中。  
  
 [!code-cpp[NVC_MFCSocketThread #&4;](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 有关详细信息，请参阅[MFC 中的 Windows 套接字](../../mfc/windows-sockets-in-mfc.md)， [Windows 套接字︰ 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxsock.h  
  
##  <a name="csocketfile"></a>CSocketFile::CSocketFile  
 构造 `CSocketFile` 对象。  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pSocket`  
 若要将附加到的套接字`CSocketFile`对象。  
  
 `bArchiveCompatible`  
 指定文件对象是否适用于`CArchive`对象。 传递**FALSE**仅当你想要使用`CSocketFile`对象在独立的方式，根据需要独立`CFile`对象，但存在一些限制。 此标志会更改如何`CArchive`对象附加到`CSocketFile`对象管理它以进行读取的缓冲区。  
  
### <a name="remarks"></a>备注  
 对象的析构函数解除之间的关联本身套接字对象超出范围或被删除的对象时。  
  
> [!NOTE]
>  一个`CSocketFile`也用作 （受限） 文件，而没有`CArchive`对象。 默认情况下，`CSocketFile`构造函数的`bArchiveCompatible`参数是**TRUE**。 这将指定文件对象是用于存档。 若要使用但未存档的文件对象，将传递**FALSE**中`bArchiveCompatible`参数。  
  
 在"兼容存档"模式下，`CSocketFile`对象提供了更好的性能并减少了的危险"死锁"。 相互关联，或公共资源等待这两个发送和接收套接字时，将发生死锁。 如果这种情况下可能会出现`CArchive`对象从事`CSocketFile`的方式与其处理`CFile`对象。 与`CFile`，存档可以假设，如果它收到更少字节数比其请求时，文件结尾为止。  
  
 与`CSocketFile`，但是，数据是基于消息; 缓冲区中可以包含多条消息，因此接收请求的字节数少于并不意味着文件结尾。 在此情况下不会阻止应用程序，因为它可能会`CFile`，它可以继续从缓冲区中读取消息，直到缓冲区为空。 [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty)函数可用于监视这种情况下对存档的缓冲区的状态。  
  
 有关详细信息的使用`CSocketFile`，请参阅文章[Windows 套接字︰ 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)和[Windows 套接字︰ 套接字的使用存档示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket 类](../../mfc/reference/casyncsocket-class.md)   
 [CSocket 类](../../mfc/reference/csocket-class.md)

