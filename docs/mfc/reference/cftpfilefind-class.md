---
title: "CFtpFileFind 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs: C++
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4fe3b188d5b03c9e727349b9e30982cf52006c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cftpfilefind-class"></a>CFtpFileFind 类
辅助 FTP 服务器的 Internet 文件搜索。  
  
## <a name="syntax"></a>语法  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|构造 `CFtpFileFind` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cftpfilefind:: Findfile](#findfile)|查找 FTP 服务器上的文件。|  
|[Cftpfilefind:: Findnextfile](#findnextfile)|继续执行从上次调用文件搜索， [FindFile](#findfile)。|  
|[CFtpFileFind::GetFileURL](#getfileurl)|获取的 URL，包括找到的文件的路径。|  
  
## <a name="remarks"></a>备注  
 `CFtpFileFind`包括成员函数来开始的搜索，找到文件，并返回 URL 或文件的其他说明性信息。  
  
 设计为 Internet 和搜索的本地文件包括其他 MFC 类[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 连同`CFtpFileFind`，这些类提供用于客户端能够确定协议或文件类型 （本地计算机或远程服务器） 的特定文件，而不考虑服务器的无缝机制。 请注意，因为 HTTP 不支持直接文件操作所需的搜索搜索 HTTP 服务器上没有任何 MFC 类。  
  
 有关如何使用`CFtpFileFind`和其他 WinInet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="example"></a>示例  
 下面的代码演示如何枚举 FTP 服务器的当前目录中的所有文件。  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxinet.h  
  
##  <a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind  
 此成员函数调用以构造`CFtpFileFind`对象。  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `pConnection`  
 指向的指针`CFtpConnection`对象。 你可以通过调用获取 FTP 连接[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)。  
  
 `dwContext`  
 上下文标识符`CFtpFileFind`对象。 请参阅**备注**有关此参数的详细信息。  
  
### <a name="remarks"></a>备注  
 默认值为`dwContext`发送到 mfc`CFtpFileFind`对象[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CFtpFileFind`对象。 你可以重写默认设置，以便为你选择的值设置的上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
### <a name="example"></a>示例  
  请参阅本主题前面的类概述中的示例。  
  
##  <a name="findfile"></a>Cftpfilefind:: Findfile  
 调用此成员函数可查找 FTP 文件。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 指向包含要查找的文件的名称的字符串的指针。 如果**NULL**，调用将执行通配符的搜索 （*）。  
  
 `dwFlags`  
 描述如何处理此会话的标志。 这些标志可以与按位 OR 运算符 (&#124;) 结合使用，并如下所示：  
  
-   即使本地缓存 INTERNET_FLAG_RELOAD 从网络中获得数据。 这是默认值标志。  
  
-   INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。  
  
-   INTERNET_FLAG_RAW_DATA 重写默认设置，以便返回原始数据 ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) FTP 的结构)。  
  
-   INTERNET_FLAG_SECURE 保护使用安全套接字层或百分比在网络上的事务 此标志将适用于仅 HTTP 请求。  
  
-   INTERNET_FLAG_EXISTING_CONNECT 如果可能，请重复使用现有连接到服务器新**FindFile**而不是创建每个请求的新会话的请求。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 在调用**FindFile**若要检索的第一个 FTP 文件，可以调用[FindNextFile](#findnextfile)以检索后续 FTP 文件。  
  
### <a name="example"></a>示例  
  请参阅本主题中前面的示例。  
  
##  <a name="findnextfile"></a>Cftpfilefind:: Findnextfile  
 调用此成员函数可继续通过调用开始文件搜索[FindFile](#findfile)成员函数。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>返回值  
 如果有多个文件; 则为非 0如果找到的文件是在目录中的最后一个，或者如果出错，则为零。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到的文件是在目录中，最后一个文件，或者如果没有任何匹配可以找到文件，`GetLastError`函数返回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>备注  
 您必须调用任何属性函数之前，至少一次调用此函数 (请参阅[CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile))。  
  
 `FindNextFile`包装的 Win32 函数[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>示例  
  请参阅本主题前面的示例。  
  
##  <a name="getfileurl"></a>CFtpFileFind::GetFileURL  
 调用此成员函数可获取指定的文件的 URL。  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件和路径的通用资源定位符 (URL)。  
  
### <a name="remarks"></a>备注  
 `GetFileURL`类似于成员函数[CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)，只不过它的形式返回 URL `ftp://moose/dir/file.txt`。  
  
## <a name="see-also"></a>请参阅  
 [CFileFind 类](../../mfc/reference/cfilefind-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)
