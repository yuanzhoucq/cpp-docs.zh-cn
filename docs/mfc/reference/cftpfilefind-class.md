---
title: CFtpFileFind 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaa080460a545e56fcb527f3b8bf4dc57e008e3c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392094"
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
|[Cftpfilefind:: Findnextfile](#findnextfile)|将继续通过以前调用文件搜索[FindFile](#findfile)。|
|[CFtpFileFind::GetFileURL](#getfileurl)|获取的 URL，包括找到的文件的路径。|

## <a name="remarks"></a>备注

`CFtpFileFind` 包含成员函数来开始搜索，找到文件，并返回的 URL 或文件的其他说明性信息。

此演示适合对于 Internet 和本地文件搜索包括其他 MFC 类[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)并[CFileFind](../../mfc/reference/cfilefind-class.md)。 连同`CFtpFileFind`，这些类提供用于客户端以查找特定文件，而不考虑服务器协议或文件类型 （本地计算机或远程服务器） 的无缝机制。 请注意，搜索 HTTP 服务器上，因为 HTTP 不支持直接进行文件操作所需的搜索没有 MFC 类。

有关如何使用详细信息`CFtpFileFind`和其他 WinInet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="example"></a>示例

下面的代码演示如何枚举在 FTP 服务器的当前目录中的所有文件。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

调用此成员函数来构造`CFtpFileFind`对象。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pConnection*<br/>
一个指向`CFtpConnection`对象。 你可以通过调用获取 FTP 连接[cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)。

*dwContext*<br/>
上下文标识符`CFtpFileFind`对象。 请参阅**备注**有关此参数的详细信息。

### <a name="remarks"></a>备注

默认值为*dwContext*发送到 mfc`CFtpFileFind`对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建`CFtpFileFind`对象。 您可以覆盖默认设置，以便将上下文标识符设置为所选的值。 上下文标识符就会归还[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供与该标识的对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

### <a name="example"></a>示例

  请参阅本主题前面的类概述中的示例。

##  <a name="findfile"></a>  Cftpfilefind:: Findfile

调用此成员函数以找到 FTP 文件。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>参数

*pstrName*<br/>
指向包含要查找的文件的名称的字符串的指针。 如果为 NULL，则调用将执行通配符搜索 （*）。

*dwFlags*<br/>
描述如何处理此会话标志。 可以使用按位 OR 运算符组合这些标志 (&#124;)，如下所示：

- 即使本地缓存 INTERNET_FLAG_RELOAD 从网络中获取数据。 这是默认标志。

- INTERNET_FLAG_DONT_CACHE 不缓存数据，本地或在任何网关。

- INTERNET_FLAG_RAW_DATA 重写默认设置，以便返回原始数据 ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) FTP 的结构)。

- INTERNET_FLAG_SECURE 保护与安全套接字层或百分比在网络上的事务 此标志为适用于仅 HTTP 请求。

- INTERNET_FLAG_EXISTING_CONNECT 如果可能，请重复使用现有连接到服务器的新`FindFile`而不是创建新的会话的每个请求的请求。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

### <a name="remarks"></a>备注

在调用`FindFile`若要检索的第一个 FTP 文件，可以调用[FindNextFile](#findnextfile)检索后续 FTP 文件。

### <a name="example"></a>示例

  请参阅本主题中前面的示例。

##  <a name="findnextfile"></a>  Cftpfilefind:: Findnextfile

调用此成员函数以继续文件搜索开始通过调用[FindFile](#findfile)成员函数。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

非零，如果有多个文件;如果找到该文件是在目录中的最后一个，或如果出错，则为零。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到该文件是在目录中的最后一个文件，或者如果没有匹配的可以找到文件，`GetLastError`函数返回 ERROR_NO_MORE_FILES。

### <a name="remarks"></a>备注

您必须至少一次调用属性的任何函数之前调用此函数 (请参阅[CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile))。

`FindNextFile` 包装 Win32 函数[FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea)。

### <a name="example"></a>示例

  请参阅本主题前面的示例。

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

调用此成员函数可获取指定文件的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

文件和路径的通用资源定位器 (URL)。

### <a name="remarks"></a>备注

`GetFileURL` 类似于此成员函数[CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)，只不过它在窗体中返回的 URL `ftp://moose/dir/file.txt`。

## <a name="see-also"></a>请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
