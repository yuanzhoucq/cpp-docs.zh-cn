---
title: CFtpFileFind 类
ms.date: 11/04/2016
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373742"
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
|[CFtp文件查找：：CFtpFile查找](#cftpfilefind)|构造 `CFtpFileFind` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFtp文件查找：查找文件](#findfile)|在 FTP 服务器上查找文件。|
|[CFtp文件查找：：查找下一个文件](#findnextfile)|继续从上一个调用[FindFile](#findfile)的文件搜索。|
|[CFtpFile查找：：获取文件URL](#getfileurl)|获取找到文件的 URL，包括路径。|

## <a name="remarks"></a>备注

`CFtpFileFind`包括开始搜索、查找文件并返回有关该文件的 URL 或其他描述性信息的成员函数。

其他MFC类专为互联网和本地文件搜索包括[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFileFind。](../../mfc/reference/cfilefind-class.md) 与`CFtpFileFind`结合 这些类为客户端提供了一个无缝机制来查找特定文件，而不管服务器协议或文件类型（本地计算机或远程服务器）。 请注意，没有用于在 HTTP 服务器上搜索的 MFC 类，因为 HTTP 不支持搜索所需的直接文件操作。

有关如何使用`CFtpFileFind`和其他 WinInet 类的详细信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="example"></a>示例

以下代码演示如何枚举 FTP 服务器当前目录中的所有文件。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtp文件查找：：CFtpFile查找

调用此成员函数以构造对象`CFtpFileFind`。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*p连接*<br/>
一个指向 `CFtpConnection` 对象的指针。 您可以通过调用 CInternetSession 获得 FTP 连接[：：获取Ftp连接](../../mfc/reference/cinternetsession-class.md#getftpconnection)。

*dwContext*<br/>
`CFtpFileFind`对象的上下文标识符。 有关此参数的详细信息，请参阅**备注**。

### <a name="remarks"></a>备注

mFC 从`CFtpFileFind`创建对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md) `CFtpFileFind`对象向对象发送*dwContext*的默认值。 您可以重写默认值，将上下文标识符设置为您选择的值。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

### <a name="example"></a>示例

  请参阅本主题前面的类概述中的示例。

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtp文件查找：查找文件

调用此成员函数以查找 FTP 文件。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>参数

*pstrName*<br/>
指向要查找的文件名称的字符串的指针。 如果 NULL，则呼叫将执行通配符搜索 （*）。

dwFlags**<br/>
描述如何处理此会话的标志。 这些标志可以与位或运算符 （&#124;） 组合，如下所示：

- INTERNET_FLAG_RELOAD从导线中获取数据，即使它是本地缓存的。 这是默认标志。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何网关中缓存数据。

- INTERNET_FLAG_RAW_DATA覆盖默认值以返回原始数据[（FTP WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)结构）。

- INTERNET_FLAG_SECURE使用安全套接字层或 PCT 保护线上的交易。 此标志仅适用于 HTTP 请求。

- INTERNET_FLAG_EXISTING_CONNECT 如果可能，请重用与服务器的现有连接以访问`FindFile`新请求，而不是为每个请求创建新会话。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

### <a name="remarks"></a>备注

调用`FindFile`以检索第一个 FTP 文件后，可以调用[FindNextFile](#findnextfile)检索后续 FTP 文件。

### <a name="example"></a>示例

  请参阅本主题中的较早示例。

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtp文件查找：：查找下一个文件

调用此成员函数以继续从调用[FindFile](#findfile)成员函数开始的文件搜索。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>返回值

如果文件更多，则非零;如果找到的文件是目录中的最后一个文件或发生错误，则为零。 要获取扩展错误信息，请致电 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。 如果找到的文件是目录中的最后一个文件，或者找不到匹配的文件，则`GetLastError`函数将返回ERROR_NO_MORE_FILES。

### <a name="remarks"></a>备注

在调用任何属性函数之前，必须至少调用此函数一次（请参阅[CFileFind：FindNextFile）。](../../mfc/reference/cfilefind-class.md#findnextfile)

`FindNextFile`包装 Win32 函数[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)。

### <a name="example"></a>示例

  请参阅本主题前面的示例。

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFile查找：：获取文件URL

调用此成员函数获取指定文件的 URL。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>返回值

通用资源定位器 （URL） 的文件和路径。

### <a name="remarks"></a>备注

`GetFileURL`类似于成员函数[CFileFind：：getFilePath，](../../mfc/reference/cfilefind-class.md#getfilepath)只不过它返回窗体`ftp://moose/dir/file.txt`中的 URL。

## <a name="see-also"></a>另请参阅

[CFileFind 类](../../mfc/reference/cfilefind-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CGopher文件查找类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 类](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile 类](../../mfc/reference/chttpfile-class.md)
