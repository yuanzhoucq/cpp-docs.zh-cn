---
title: "CGopherFileFind 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
dev_langs: C++
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06b71e3cbebc7ed052fafff077d951a7f3ade810
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind 类
辅助 Gopher 服务器的 Internet 文件搜索。  
  
> [!NOTE]
>  类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成员具有已弃用，因为它们不能在 Windows XP 平台上，但它们将继续在早期版本的平台上正常工作。  
  
## <a name="syntax"></a>语法  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|构造 `CGopherFileFind` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CGopherFileFind::FindFile](#findfile)|查找 gopher 服务器上的文件。|  
|[CGopherFileFind::FindNextFile](#findnextfile)|继续执行从上次调用文件搜索， [FindFile](#findfile)。|  
|[CGopherFileFind::GetCreationTime](#getcreationtime)|获取指定的文件的创建的时间。|  
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|获取上次访问指定的文件的时间。|  
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|获取上次写入指定的文件的时间。|  
|[CGopherFileFind::GetLength](#getlength)|获取找到的文件，以字节为单位的长度。|  
|[CGopherFileFind::GetLocator](#getlocator)|获取`CGopherLocator`对象。|  
|[CGopherFileFind::GetScreenName](#getscreenname)|获取 gopher 屏幕的名称。|  
|[CGopherFileFind::IsDots](#isdots)|循环访问文件时的当前目录及其父目录标记的测试。|  
  
## <a name="remarks"></a>备注  
 `CGopherFileFind`包括成员函数来开始的搜索，找到文件，并返回文件的 URL。  
  
 设计为 Internet 和搜索的本地文件包括其他 MFC 类[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 连同`CGopherFileFind`，这些类提供无缝的机制，用户若要查找特定的文件，而不考虑服务器协议、 文件类型或位置 （本地计算机或远程服务器。）请注意，因为 HTTP 不支持直接文件操作所需的搜索搜索 HTTP 服务器上没有任何 MFC 类。  
  
> [!NOTE]
> `CGopherFileFind`不支持其基本类的下列成员函数[CFileFind](../../mfc/reference/cfilefind-class.md):  
  
- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)  
  
- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)  
  
- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)  
  
- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)  
  
- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)  
  
 此外，如果用于`CGopherFileFind`、`CFileFind`成员函数[IsDots](../../mfc/reference/cfilefind-class.md#isdots)始终**FALSE**。  
  
 有关如何使用`CGopherFileFind`和其他 WinInet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## <a name="requirements"></a>要求  
 **标头：** afxinet.h  
  
##  <a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind  
 此成员函数调用以构造`CGopherFileFind`对象。  
  
```  
explicit CGopherFileFind(
    CGopherConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `pConnection`  
 指向的指针[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。  
  
 `dwContext`  
 操作上下文标识符。 请参阅**备注**有关详细信息`dwContext`。  
  
### <a name="remarks"></a>备注  
 默认值为`dwContext`发送到 mfc`CGopherFileFind`对象[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CGopherFileFind`对象。 构造时`CGopherFileFind`对象，您可以重写默认设置，以便为你选择的值设置的上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="findfile"></a>CGopherFileFind::FindFile  
 调用此成员函数可查找 gopher 文件。  
  
```  
virtual BOOL FindFile(
    CGopherLocator& refLocator,  
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

 
virtual BOOL FindFile(
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>参数  
 `refLocator`  
 对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。  
  
 *pstrString*  
 指向包含的文件名称的字符串的指针。  
  
 `dwFlags`  
 描述如何处理此会话的标志。 有效标志包括：  
  
-   即使本地缓存，INTERNET_FLAG_RELOAD 从远程服务器获取数据。  
  
-   INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。  
  
-   使用安全套接字层或百分比在网络上 INTERNET_FLAG_SECURE 请求安全事务 此标志将适用于仅 HTTP 请求。  
  
-   INTERNET_FLAG_USE_EXISTING 如果可能，请重复使用现有连接到服务器新**FindFile**请求，而不是创建每个请求的新会话。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 在调用**FindFile**若要检索的第一个 gopher 对象，可以调用[FindNextFile](#findnextfile)以检索后续 gopher 文件。  
  
##  <a name="findnextfile"></a>CGopherFileFind::FindNextFile  
 调用此成员函数可继续通过调用开始文件搜索[CGopherFileFind::FindFile](#findfile)。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>返回值  
 如果有多个文件; 则为非 0如果找到的文件是在目录中的最后一个，或者如果出错，则为零。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到的文件是在目录中，最后一个文件，或者如果没有任何匹配可以找到文件，`GetLastError`函数返回 ERROR_NO_MORE_FILES。  
  
##  <a name="getcreationtime"></a>CGopherFileFind::GetCreationTime  
 获取当前文件的创建时间。  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含已创建了文件的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetCreationTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CGopherFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetCreationTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 在某些操作系统上返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
##  <a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime  
 获取上次访问指定的文件的时间。  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>参数  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含上一次访问该文件的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetLastAccessTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CGopherFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastAccessTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 在某些操作系统上返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
##  <a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime  
 获取该文件已更改的最后一个时间。  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含文件上次写入到的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetLastWriteTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CGopherFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastWriteTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 在某些操作系统上返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
##  <a name="getlength"></a>CGopherFileFind::GetLength  
 调用此成员函数要获取长度，以字节为单位，找到的文件。  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 找到文件的长度，以字节为单位。  
  
### <a name="remarks"></a>备注  
 `GetLength`使用 Win32 结构[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)来获取文件大小的值以字节为单位。  
  
> [!NOTE]
>  截至 MFC 7.0`GetLength`支持 64 位整数类型。 用此较新版本的库生成的之前存在代码可能会导致截断警告。  
  
### <a name="example"></a>示例  
  请参阅示例[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) （基类实现）。  
  
##  <a name="getlocator"></a>CGopherFileFind::GetLocator  
 调用此成员函数可获取[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象[FindFile](#findfile)使用查找 gopher 文件。  
  
```  
CGopherLocator GetLocator() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 `CGopherLocator` 对象。  
  
##  <a name="getscreenname"></a>CGopherFileFind::GetScreenName  
 调用此成员函数可获取 gopher 屏幕的名称。  
  
```  
CString GetScreenName() const;  
```  
  
### <a name="return-value"></a>返回值  
 Gopher 屏幕的名称。  
  
##  <a name="isdots"></a>CGopherFileFind::IsDots  
 循环访问文件时的当前目录及其父目录标记的测试。  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果找到的文件具有名称"。".."，指示找到的文件是实际的目录。 否则为 0。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsDots`。  
  
## <a name="see-also"></a>另请参阅  
 [CFileFind 类](../../mfc/reference/cfilefind-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind 类](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)
