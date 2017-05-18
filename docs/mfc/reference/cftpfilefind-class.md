---
title: "CFtpFileFind 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs:
- C++
helpviewer_keywords:
- CFtpFileFind class
- file searches [C++]
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e84282cc2f22e813ea44318d497c7e32e3280d8
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cftpfilefind-class"></a>CFtpFileFind 类
辅助 FTP 服务器的 Internet 文件搜索。  
  
## <a name="syntax"></a>语法  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|构造 `CFtpFileFind` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Cftpfilefind:: Findfile](#findfile)|查找 FTP 服务器上的文件。|  
|[Cftpfilefind:: Findnextfile](#findnextfile)|继续执行文件搜索的以前调用从[FindFile](#findfile)。|  
|[CFtpFileFind::GetFileURL](#getfileurl)|获取的 URL，包括找到的文件的路径。|  
  
## <a name="remarks"></a>备注  
 `CFtpFileFind`包含成员函数开始的搜索、 查找文件，并将返回的 URL 或文件的其他说明性信息。  
  
 面向 Internet 和搜索的本地文件包括其他 MFC 类[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind](../../mfc/reference/cfilefind-class.md)。 与`CFtpFileFind`，这些类提供了用于客户端来查找特定文件，而不考虑服务器协议或文件类型 （本地计算机或远程服务器） 的无缝机制。 请注意，因为 HTTP 不支持直接文件操作所需的搜索，搜索 HTTP 服务器上的任何 MFC 类。  
  
 有关如何使用`CFtpFileFind`和其他 WinInet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="example"></a>示例  
 下面的代码演示如何枚举 FTP 服务器的当前目录中的所有文件。  
  
 [!code-cpp[NVC_MFCWinInet #&8;](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind  
 调用此成员函数来构造`CFtpFileFind`对象。  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `pConnection`  
 一个指向`CFtpConnection`对象。 通过调用获取 FTP 连接[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)。  
  
 `dwContext`  
 上下文标识符`CFtpFileFind`对象。 请参阅**备注**有关此参数的详细信息。  
  
### <a name="remarks"></a>备注  
 默认值为`dwContext`发送到 mfc`CFtpFileFind`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CFtpFileFind`对象。 您可以重写默认设置，以便为您选择的值设置上下文标识符。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供对它标识的对象的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
### <a name="example"></a>示例  
  请参见本主题中前面的类概述中的示例。  
  
##  <a name="findfile"></a>Cftpfilefind:: Findfile  
 调用该成员函数以找到 FTP 文件。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 指向包含要查找的文件的名称的字符串的指针。 如果**NULL**，调用将执行通配符搜索 （*）。  
  
 `dwFlags`  
 描述如何处理此会话的标志。 这些标志可以使用按位 OR 运算符 (|) 组合，如下︰  
  
-   即使在本地进行缓存，INTERNET_FLAG_RELOAD 通过网络获取数据。 这是默认标志。  
  
-   INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。  
  
-   INTERNET_FLAG_RAW_DATA 重写默认设置，以便返回原始数据 ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) FTP 的结构)。  
  
-   INTERNET_FLAG_SECURE 保护在使用安全套接字层或 （百分比） 网络上的事务 此标志为适用于仅 HTTP 请求。  
  
-   INTERNET_FLAG_EXISTING_CONNECT 如果可能，请重复使用现有连接到服务器的新**FindFile**请求而不是创建每个请求一个新会话。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 在调用**FindFile**若要检索的第一个 FTP 文件，您可以调用[FindNextFile](#findnextfile)检索后续 FTP 文件。  
  
### <a name="example"></a>示例  
  请参阅本主题中前面的示例。  
  
##  <a name="findnextfile"></a>Cftpfilefind:: Findnextfile  
 调用此成员函数以继续时，首先执行调用的文件搜索[FindFile](#findfile)成员函数。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果有多个文件;如果找到该文件是在目录中的最后一个，或者出现错误，则为零。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到该文件是在目录中，最后一个文件，或者如果没有匹配可以找到文件，`GetLastError`函数将返回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>备注  
 您必须在调用属性的任何函数之前至少一次调用此函数 (请参阅[CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile))。  
  
 `FindNextFile`封装的 Win32 函数[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>示例  
  请参阅本主题前面的示例。  
  
##  <a name="getfileurl"></a>CFtpFileFind::GetFileURL  
 调用此成员函数可获取指定的文件的 URL。  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件和路径的通用资源定位器 (URL)。  
  
### <a name="remarks"></a>备注  
 `GetFileURL`类似于成员函数[CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)，只不过它的形式返回 URL `ftp://moose/dir/file.txt`。  
  
## <a name="see-also"></a>另请参阅  
 [CFileFind 类](../../mfc/reference/cfilefind-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)

