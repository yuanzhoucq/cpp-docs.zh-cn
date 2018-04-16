---
title: "CInternetFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
dev_langs:
- C++
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1e4b05e2aceb8fb4c8a4abed0dd6038fff6cfee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetfile-class"></a>CInternetFile 类
允许访问在使用 Internet 协议的远程系统上的文件。  
  
## <a name="syntax"></a>语法  
  
```  
class CInternetFile : public CStdioFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](#cinternetfile)|构造 `CInternetFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|关闭该文件，忽略所有警告和错误。|  
|[CInternetFile::Close](#close)|关闭`CInternetFile`并释放其资源。|  
|[CInternetFile::Flush](#flush)|刷新写入缓冲区的内容，并确保内存中的数据写入到目标计算机。|  
|[CInternetFile::GetLength](#getlength)|返回文件的大小。|  
|[Cinternetfile:: Read](#read)|读取指定的字节数。|  
|[CInternetFile::ReadString](#readstring)|读取字符的流。|  
|[CInternetFile::Seek](#seek)|在打开的文件指针重新定位。|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|设置要从中读取数据的缓冲区的大小。|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|设置缓冲区的大小将在其中写入数据。|  
|[CInternetFile::Write](#write)|写入指定的字节数。|  
|[CInternetFile::WriteString](#writestring)|以 null 结尾的字符串写入文件。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Internet 句柄强制转换运算符。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|文件的句柄。|  
  
## <a name="remarks"></a>备注  
 提供的基类[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile](../../mfc/reference/cgopherfile-class.md)文件类。 切勿创建`CInternetFile`直接对象。 相反，通过调用创建的对象及其派生类之一[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您还可以创建`CInternetFile`对象通过调用[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。  
  
 `CInternetFile`成员函数**打开**， `LockRange`， `UnlockRange`，和`Duplicate`未实现`CInternetFile`。 如果你对调用这些函数`CInternetFile`对象，则将会出现[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要了解有关如何`CInternetFile`工作与其他 MFC Internet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxinet.h  
  
##  <a name="abort"></a>CInternetFile::Abort  
 关闭与此对象关联的文件，并使该文件进行读取或写入不可用。  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>备注  
 如果您未在销毁对象之前关闭该文件，析构函数为你将其关闭。  
  
 当处理异常、**中止**区别[关闭](#close)在两个重要方面。 首先，**中止**因为它会忽略失败函数不会在失败引发异常。 第二个，**中止**不**断言**如果文件尚未打开或在以前已关闭。  
  
##  <a name="cinternetfile"></a>CInternetFile::CInternetFile  
 此成员函数调用时`CInternetFile`创建对象。  
  
```  
CInternetFile(
    HINTERNET hFile,  
    LPCTSTR pstrFileName,  
    CInternetConnection* pConnection,  
    BOOL bReadMode);

 
CInternetFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrFileName,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext,  
    BOOL bReadMode);
```  
  
### <a name="parameters"></a>参数  
 `hFile`  
 Internet 文件的句柄。  
  
 `pstrFileName`  
 指向包含的文件名称的字符串的指针。  
  
 `pConnection`  
 指向的指针[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)对象。  
  
 *bReadMode*  
 指示文件是否为只读的。  
  
 `hSession`  
 Internet 会话句柄。  
  
 `pstrServer`  
 指向包含的服务器名称的字符串的指针。  
  
 `dwContext`  
 上下文标识符`CInternetFile`对象。 请参阅[WinInet 基础知识](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
### <a name="remarks"></a>备注  
 切勿创建`CInternetFile`直接对象。 相反，通过调用创建的对象及其派生类之一[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您还可以创建`CInternetFile`对象通过调用[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。  
  
##  <a name="close"></a>CInternetFile::Close  
 关闭`CInternetFile`并释放任何其资源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 如果文件已打开进行写入，则隐式调用[刷新](#flush)以确保所有缓冲数据写入到主机。 应调用**关闭**在完成使用文件时。  
  
##  <a name="flush"></a>CInternetFile::Flush  
 调用此成员函数以刷新写入缓冲区的内容。  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>备注  
 使用`Flush`为确保内存中的所有数据实际已都写入到目标计算机，然后以确保与主机机你事务已完成。 `Flush`仅对有效`CInternetFile`对象打开以进行写入。  
  
##  <a name="getlength"></a>CInternetFile::GetLength  
 返回文件的大小。  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>CInternetFile::m_hFile  
 与此对象关联的文件句柄。  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>CInternetFile::operator HINTERNET  
 使用此运算符将获取当前的 Internet 会话的 Windows 句柄。  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>Cinternetfile:: Read  
 调用此成员函数以将指定字节数 `nCount` 读入给定内存（从 `lpvBuf` 开始）。  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 指向将文件数据读取到的内存地址的指针。  
  
 `nCount`  
 要写入的字节数。  
  
### <a name="return-value"></a>返回值  
 传输到缓冲区的字节数。 如果已到达文件末尾，则返回值可能小于 `nCount`。  
  
### <a name="remarks"></a>备注  
 函数返回实际读取的字节数（一个数字，在文件结束时可能小于 `nCount`）。 如果在读取文件时发生错误，该函数将引发[CInternetException](../../mfc/reference/cinternetexception-class.md)描述错误的对象。 请注意，不会将越过文件末尾的读取视为错误，不会引发异常。  
  
 若要确保检索所有数据，应用程序必须继续调用**cinternetfile:: Read**方法，直到该方法返回零。  
  
##  <a name="readstring"></a>CInternetFile::ReadString  
 调用此成员函数可读取的字符流，直到它找到一个换行符。  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向一个字符串，它将接收所读取的行的指针。  
  
 `nMax`  
 最大要读取的字符数。  
  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收读取的行的对象。  
  
### <a name="return-value"></a>返回值  
 指向包含从检索到的纯文本数据的缓冲区的指针[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象。 无论传递给此方法的缓冲区的数据类型，它不在数据 （例如，转换为 Unicode） 时执行任何操作，因此必须将返回的数据映射到结构希望，就像**void\*** 返回类型。  
  
 **NULL**如果文件尾已访问而无需读取任何数据; 或者如果布尔值、 **FALSE**如果而无需读取任何数据已到达最终的文件。  
  
### <a name="remarks"></a>备注  
 该函数将生成的行置于所引用的内存`pstr`参数。 它将停止读取字符时达到最大字符数，指定`nMax`。 缓冲区始终接收终止 null 字符。  
  
 如果调用`ReadString`而无需首先调用[SetReadBufferSize](#setreadbuffersize)，你将获得 4096 个字节的缓冲区。  
  
##  <a name="seek"></a>CInternetFile::Seek  
 调用此成员函数可将指针重新定位在先前已打开的文件中。  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>参数  
 `lOffset`  
 以字节为单位来移动文件中的读/写指针的偏移量。  
  
 `nFrom`  
 偏移量的相对引用。 必须是以下值之一：  
  
- **CFile::begin**将文件指针移`lOff`转发中文件的开头的字节。  
  
- **CFile::current**将文件指针移`lOff`个字节从文件中的当前位置。  
  
- **CFile::end**将文件指针移`lOff`从文件末尾的字节。 `lOff`必须是负值以查找到现有的文件;正值将查找该文件的末尾。  
  
### <a name="return-value"></a>返回值  
 新字节偏移量从文件的开头，如果所请求的位置是合法的;否则，值是不确定和[CInternetException](../../mfc/reference/cinternetexception-class.md)引发对象。  
  
### <a name="remarks"></a>备注  
 `Seek`函数允许随机访问文件的内容通过移动指针指定的量，绝对或相对。 在查找期间实际不读取任何数据。  
  
 目前，对此成员函数的调用仅支持与相关联数据`CHttpFile`对象。 不支持 FTP 或 gopher 请求。 如果调用`Seek`这些不受支持的服务之一，它将传递回你的 Win32 错误代码**ERROR_INTERNET_INVALID_OPERATION**。  
  
 当打开文件时，文件指针位于偏移量为 0，文件的开头。  
  
> [!NOTE]
>  使用`Seek`可能会导致隐式调用[刷新](#flush)。  
  
### <a name="example"></a>示例  
  请参阅基类实现的示例 ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek))。  
  
##  <a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize  
 调用此成员函数，可使用的临时读取缓冲区的大小设置`CInternetFile`-派生对象。  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>参数  
 *nReadSize*  
 所需的缓冲区大小（以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 基础的 WinInet Api 不要执行缓冲，允许你的应用程序能够高效，而不考虑要读取的数据量读取数据的缓冲区大小，因此选择。 如果每个调用[读取](#read)通常涉及大型 aount 的数据 （例如，四个或多个千字节为单位），不应需要缓冲区。 但是，如果调用**读取**获取小块数据，或者如果你使用[ReadString](#readstring)来一次读取的各个行，则读取的缓冲区提高应用程序性能。  
  
 默认情况下，`CInternetFile`对象不提供任何缓冲以进行读取。 如果调用此成员函数，你必须确保已打开文件进行读取访问权限。  
  
 你可以在任何时候，增加缓冲区大小，但收缩缓冲区将产生任何影响。 如果调用[ReadString](#readstring)而无需首先调用`SetReadBufferSize`，你将获得 4096 个字节的缓冲区。  
  
##  <a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize  
 调用此成员函数，可使用的临时写入缓冲区的大小设置`CInternetFile`-派生对象。  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>参数  
 *nWriteSize*  
 缓冲区的大小（以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 基础 WinInet Api 不进行缓冲，因此选择允许你的应用程序写入高效地无论要写入的数据量的数据的缓冲区大小。 如果每个调用[编写](#write)通常涉及大量的数据 （例如，四个或多个千字节为单位一次），不应需要缓冲区。 但是，如果调用[编写](#write)若要编写小块数据，写入缓冲区，可提高应用程序的性能。  
  
 默认情况下，`CInternetFile`对象不提供任何缓冲以进行写入。 如果调用此成员函数，你必须确保已打开文件进行写访问权限。 你可以在任何时候，更改写入缓冲区的大小，但这样做会导致隐式调用[刷新](#flush)。  
  
##  <a name="write"></a>CInternetFile::Write  
 调用此成员函数可写入到给定的内存中， `lpvBuf`，则指定的字节数`nCount`。  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 指向要写入的第一个字节的指针。  
  
 `nCount`  
 指定要写入字节数。  
  
### <a name="remarks"></a>备注  
 如果将数据写入时出现任何错误，该函数将引发[CInternetException](../../mfc/reference/cinternetexception-class.md)对错误进行描述的对象。  
  
##  <a name="writestring"></a>CInternetFile::WriteString  
 此函数将以 null 结尾的字符串写入关联的文件。  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>参数  
 `pstr`  
 指向包含要写入的内容的字符串的指针。  
  
### <a name="remarks"></a>备注  
 如果将数据写入时出现任何错误，该函数将引发[CInternetException](../../mfc/reference/cinternetexception-class.md)对错误进行描述的对象。  
  
## <a name="see-also"></a>请参阅  
 [CStdioFile 类](../../mfc/reference/cstdiofile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)
