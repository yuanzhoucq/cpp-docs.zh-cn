---
title: CInternetFile 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 68a0a0f35d1a1f4519401080f9f207bf76c87079
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505901"
---
# <a name="cinternetfile-class"></a>CInternetFile 类

允许访问使用 Internet 协议的远程系统上的文件。

## <a name="syntax"></a>语法

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|构造 `CInternetFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CInternetFile::Abort](#abort)|关闭文件，忽略所有警告和错误。|
|[CInternetFile::Close](#close)|`CInternetFile`关闭并释放其资源。|
|[CInternetFile::Flush](#flush)|刷新写入缓冲区的内容，确保内存中的数据写入目标计算机。|
|[CInternetFile::GetLength](#getlength)|返回文件的大小。|
|[CInternetFile::Read](#read)|读取指定字节数。|
|[CInternetFile::ReadString](#readstring)|读取字符流。|
|[CInternetFile::Seek](#seek)|重新定位打开文件中的指针。|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|设置将读取数据的缓冲区的大小。|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|设置将写入数据的缓冲区的大小。|
|[CInternetFile::Write](#write)|写入指定字节数。|
|[CInternetFile::WriteString](#writestring)|将以 null 结尾的字符串写入文件。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CInternetFile：： operator HINTERNET](#operator_hinternet)|Internet 句柄的转换运算符。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|文件的句柄。|

## <a name="remarks"></a>备注

提供[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile](../../mfc/reference/cgopherfile-class.md)文件类的基类。 永远不会直接`CInternetFile`创建对象。 而是通过调用[CGopherConnection：： OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：： OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)来创建其派生类之一的对象。 还可以通过调用`CInternetFile` [CFtpConnection：： OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)来创建对象。

`LockRange` `Open` `UnlockRange` `Duplicate`不为`CInternetFile` 实现的成员函数`CInternetFile`、、和。 如果在`CInternetFile`对象上调用这些函数，则将获得一个[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

若要了解有关如何`CInternetFile`使用其他 MFC Internet 类的详细信息，请参阅文章[使用 WinInet 进行 Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>要求

**标头：** afxinet。h

##  <a name="abort"></a>CInternetFile：： Abort

关闭与此对象关联的文件，并使该文件不可用于读取或写入。

```
virtual void Abort();
```

### <a name="remarks"></a>备注

如果在销毁对象之前未关闭文件，析构函数将关闭该文件。

在处理异常时`Abort` ，与[关闭](#close)在两个重要方面有所不同。 首先， `Abort`函数不会对失败引发异常，因为它忽略失败。 其次， `Abort`不**断言**文件是否已打开或之前已关闭。

##  <a name="cinternetfile"></a>CInternetFile：： CInternetFile

当创建`CInternetFile`对象时，将调用此成员函数。

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

*hFile*<br/>
Internet 文件的句柄。

*pstrFileName*<br/>
指向包含文件名的字符串的指针。

*pConnection*<br/>
指向[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)对象的指针。

*bReadMode*<br/>
指示文件是否为只读。

*hSession*<br/>
Internet 会话的句柄。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*dwContext*<br/>
`CInternetFile`对象的上下文标识符。 有关上下文标识符的详细信息，请参阅[WinInet 基础知识](../../mfc/wininet-basics.md)。

### <a name="remarks"></a>备注

永远不会直接`CInternetFile`创建对象。 而是通过调用[CGopherConnection：： OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：： OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)来创建其派生类之一的对象。 还可以通过调用`CInternetFile` [CFtpConnection：： OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)来创建对象。

##  <a name="close"></a>CInternetFile：： Close

`CInternetFile`关闭并释放其任何资源。

```
virtual void Close();
```

### <a name="remarks"></a>备注

如果文件已打开以进行写入，则会进行隐式调用[以确保](#flush)所有缓冲的数据都写入主机。 使用完文件`Close`后，应调用。

##  <a name="flush"></a>  CInternetFile::Flush

调用此成员函数以刷新写入缓冲区的内容。

```
virtual void Flush();
```

### <a name="remarks"></a>备注

使用`Flush`以确保内存中的所有数据都已实际写入目标计算机，并确保您的主计算机上的事务已完成。 `Flush`仅对`CInternetFile`打开以进行写入的对象有效。

##  <a name="getlength"></a>CInternetFile：： GetLength

返回文件的大小。

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>CInternetFile：： m_hFile

与此对象关联的文件的句柄。

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>CInternetFile：： operator HINTERNET

使用此运算符可获取当前 Internet 会话的 Windows 句柄。

```
operator HINTERNET() const;
```

##  <a name="read"></a>CInternetFile：： Read

调用此成员函数以读取给定的内存（从*lpvBuf*开始，到指定的字节数， *nCount*）。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向将文件数据读取到的内存地址的指针。

*nCount*<br/>
要写入的字节数。

### <a name="return-value"></a>返回值

传输到缓冲区的字节数。 如果已到达文件末尾，则返回值可能小于*nCount* 。

### <a name="remarks"></a>备注

函数返回实际读取的字节数，如果文件结束，则为可能小于*nCount*的数字。 如果读取文件时出现错误，该函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。 请注意，不会将越过文件末尾的读取视为错误，不会引发异常。

若要确保检索所有数据，应用程序必须继续调用`CInternetFile::Read`方法，直到该方法返回零。

##  <a name="readstring"></a>CInternetFile：： ReadString

调用此成员函数以读取字符流，直到它找到一个换行符。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>参数

*pstr*<br/>
指向将接收正在读取的行的字符串的指针。

*nMax*<br/>
要读取的最大字符数。

*rString*<br/>
对接收读取行的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

指向缓冲区的指针，该缓冲区包含从[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象检索到的普通数据。 无论传递到此方法的缓冲区的数据类型如何，它都不会对数据执行任何操作（例如，转换为 Unicode），因此必须将返回的数据映射到所需的结构，就像**void** <strong>\*</strong>类型为返回.

如果在未读取任何数据的情况下到达文件尾，则为 NULL;或者，如果已到达文件尾但未读取任何数据，则为 FALSE。

### <a name="remarks"></a>备注

函数将生成的行放入*pstr*参数所引用的内存。 它在达到最大字符数（由*n 每天*指定）时，它将停止读取字符。 缓冲区始终接收一个终止 null 字符。

如果在不`ReadString`首先调用[SetReadBufferSize](#setreadbuffersize)的情况下调用，将得到4096字节的缓冲区。

##  <a name="seek"></a>CInternetFile：： Seek

调用此成员函数以将指针重定位到以前打开的文件中。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>参数

*lOffset*<br/>
偏移量（以字节为单位），用于移动文件中的读/写指针。

*nFrom*<br/>
偏移量的相对引用。 必须是下列值之一：

- `CFile::begin`将文件指针*lOff*字节从文件开头向前移动。

- `CFile::current`将文件指针从文件中的当前位置移*lOff*字节。

- `CFile::end`将文件指针*lOff*字节移到文件末尾。 要查找现有文件， *lOff*必须为负数;正值将在文件末尾进行查找。

### <a name="return-value"></a>返回值

如果请求的位置合法，则为从文件开头开始的新字节偏移量;否则，该值为 undefined，并引发[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

`Seek`函数可通过将指针移动到指定的量（绝对或相对）来允许对文件内容进行随机访问。 在查找期间，不会实际读取任何数据。

目前，只有与`CHttpFile`对象相关联的数据才支持调用此成员函数。 FTP 或 gopher 请求不支持此方法。 如果对其中`Seek`一项不受支持的服务进行调用，则会将你传回 Win32 错误代码 ERROR_INTERNET_INVALID_OPERATION。

打开文件时，文件指针将在偏移量0处（文件开头）。

> [!NOTE]
>  使用`Seek`可能导致隐式调用[刷新](#flush)。

### <a name="example"></a>示例

  请参阅基类实现（ [CFile：： Seek](../../mfc/reference/cfile-class.md#seek)）的示例。

##  <a name="setreadbuffersize"></a>CInternetFile：： SetReadBufferSize

调用此成员函数可设置由`CInternetFile`派生对象使用的临时读取缓冲区的大小。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>参数

*nReadSize*<br/>
所需的缓冲区大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

底层 WinInet Api 不会执行缓冲，因此，请选择允许应用程序有效读取数据的缓冲区大小，而不考虑要读取的数据量。 如果对[读取](#read)的每次调用通常都涉及到大 aount 的数据（例如，4 kb 或更大），则不应使用缓冲区。 但是，如果调用`Read`来获取小块数据，或者使用[ReadString](#readstring)一次读取单独的行，则读取缓冲区会提高应用程序性能。

默认情况下， `CInternetFile`对象不提供任何要读取的缓冲。 如果调用此成员函数，则必须确保已打开该文件以进行读访问。

您可以随时增加缓冲区大小，但收缩缓冲区将不起作用。 如果调用[ReadString](#readstring)而不先调用`SetReadBufferSize`，则会收到4096字节的缓冲区。

##  <a name="setwritebuffersize"></a>CInternetFile：： SetWriteBufferSize

调用此成员函数可设置由`CInternetFile`派生对象使用的临时写入缓冲区的大小。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>参数

*nWriteSize*<br/>
缓冲区的大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，则可以调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)来确定错误的原因。

### <a name="remarks"></a>备注

底层 WinInet Api 不会执行缓冲，因此选择允许应用程序有效写入数据的缓冲区大小，而不考虑要写入的数据量。 如果对[写入](#write)的每个调用通常涉及大量数据（例如，一次使用四个或更多的 kb），则不应需要缓冲区。 但是，如果调用[write](#write)来写入少量数据块，则写入缓冲区会提高应用程序的性能。

默认情况下， `CInternetFile`对象不提供任何要写入的缓冲。 如果调用此成员函数，则必须确保已打开文件以进行写入访问。 你可以随时更改写入缓冲区的大小，但这样做会导致隐式调用[刷新](#flush)。

##  <a name="write"></a>CInternetFile：： Write

调用此成员函数以写入给定的内存*lpvBuf*，指定的字节数*nCount*。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向要写入的第一个字节的指针。

*nCount*<br/>
指定要写入的字节数。

### <a name="remarks"></a>备注

如果在写入数据时出现任何错误，函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

##  <a name="writestring"></a>CInternetFile：： WriteString

此函数将以 null 结尾的字符串写入关联的文件。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>参数

*pstr*<br/>
指向字符串的指针，该字符串包含要写入的内容。

### <a name="remarks"></a>备注

如果在写入数据时出现任何错误，函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

## <a name="see-also"></a>请参阅

[CStdioFile 类](../../mfc/reference/cstdiofile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)
