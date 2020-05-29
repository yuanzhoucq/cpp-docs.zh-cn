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
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372390"
---
# <a name="cinternetfile-class"></a>CInternetFile 类

允许访问使用 Internet 协议的远程系统上的文件。

## <a name="syntax"></a>语法

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[C互联网文件：C互联网文件](#cinternetfile)|构造 `CInternetFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 互联网文件：：中止](#abort)|关闭文件，忽略所有警告和错误。|
|[C互联网文件：关闭](#close)|关闭 和`CInternetFile`释放其资源。|
|[C互联网文件：Flush](#flush)|刷新写入缓冲区的内容，并确保内存中的数据写入目标计算机。|
|[C 互联网文件：获取长度](#getlength)|返回文件的大小。|
|[C 互联网文件：阅读](#read)|读取指定的字节数。|
|[C互联网文件：：阅读字符串](#readstring)|读取字符流。|
|[C 互联网文件：查找](#seek)|将指针重新定位到打开的文件中。|
|[C 互联网文件：：设置读取缓冲区大小](#setreadbuffersize)|设置将读取数据的缓冲区的大小。|
|[C 互联网文件：：设置写入缓冲区大小](#setwritebuffersize)|设置将写入数据的缓冲区的大小。|
|[C互联网文件：写入](#write)|写入指定的字节数。|
|[C互联网文件：：写入字符串](#writestring)|将 null 终止的字符串写入文件。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C互联网文件：：操作员 HINTERNET](#operator_hinternet)|互联网句柄的铸造运算符。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[C互联网文件：：m_hFile](#m_hfile)|文件的句柄。|

## <a name="remarks"></a>备注

为[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile 文件](../../mfc/reference/cgopherfile-class.md)类提供基类。 您从不直接创建`CInternetFile`对象。 相反，通过调用[CGopherConnection：：打开文件](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：：打开请求](../../mfc/reference/chttpconnection-class.md#openrequest)，创建其派生类之一的对象。 您还可以通过调用`CInternetFile`[CFtpConnection：：打开文件](../../mfc/reference/cftpconnection-class.md#openfile)来创建对象。

成员`CInternetFile``Open`函数`LockRange` `UnlockRange`、 和`Duplicate`未为`CInternetFile`实现 。 如果在`CInternetFile`对象上调用这些函数，您将获得[CNot 支持异常](../../mfc/reference/cnotsupportedexception-class.md)。

要了解有关如何`CInternetFile`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>C 互联网文件：：中止

关闭与此对象关联的文件，并使该文件无法读取或写入。

```
virtual void Abort();
```

### <a name="remarks"></a>备注

如果在销毁对象之前尚未关闭该文件，析构函数将为您关闭该文件。

在处理异常时，`Abort`从两个重要方面与[Close](#close)不同。 首先，函数`Abort`不会在失败时引发异常，因为它会忽略故障。 其次，`Abort`如果文件尚未打开或以前已关闭，则不**断言**。

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>C互联网文件：C互联网文件

创建`CInternetFile`对象时将调用此成员函数。

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
互联网文件的句柄。

*pstrFile名称*<br/>
指向包含文件名的字符串的指针。

*p连接*<br/>
指向[CInternetConnect](../../mfc/reference/cinternetconnection-class.md)对象的指针。

*bReadMode*<br/>
指示文件是否为只读文件。

*h 会话*<br/>
互联网会话的句柄。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*dwContext*<br/>
`CInternetFile`对象的上下文标识符。 有关上下文标识符的详细信息，请参阅[WinInet 基础知识](../../mfc/wininet-basics.md)。

### <a name="remarks"></a>备注

您从不直接创建`CInternetFile`对象。 相反，通过调用[CGopherConnection：：打开文件](../../mfc/reference/cgopherconnection-class.md#openfile)或[CHttpConnection：：打开请求](../../mfc/reference/chttpconnection-class.md#openrequest)，创建其派生类之一的对象。 您还可以通过调用`CInternetFile`[CFtpConnection：：打开文件](../../mfc/reference/cftpconnection-class.md#openfile)来创建对象。

## <a name="cinternetfileclose"></a><a name="close"></a>C互联网文件：关闭

关闭 和`CInternetFile`释放其任何资源。

```
virtual void Close();
```

### <a name="remarks"></a>备注

如果文件已打开以进行写入，则存在对[Flush](#flush)的隐式调用，以确保将所有缓冲数据写入主机。 使用完文件`Close`后，应调用。

## <a name="cinternetfileflush"></a><a name="flush"></a>C互联网文件：Flush

调用此成员函数以刷新写入缓冲区的内容。

```
virtual void Flush();
```

### <a name="remarks"></a>备注

用于`Flush`确保内存中的所有数据实际上已写入目标计算机，并确保与主机的事务已完成。 `Flush`仅在打开用于写入`CInternetFile`的对象上有效。

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>C 互联网文件：获取长度

返回文件的大小。

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>C互联网文件：：m_hFile

与此对象关联的文件的句柄。

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>C互联网文件：：操作员 HINTERNET

使用此运算符获取当前 Internet 会话的 Windows 句柄。

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>C 互联网文件：阅读

调用此成员函数读取到给定的内存中，从*lpvBuf*开始，指定字节数*nCount*。

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

传输到缓冲区的字节数。 如果达到文件结尾，则返回值可能小于*nCount。*

### <a name="remarks"></a>备注

函数返回实际读取的字节数 - 如果文件结束时，该数字可能小于*nCount。* 如果在读取文件时发生错误，该函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。 请注意，不会将越过文件末尾的读取视为错误，不会引发异常。

为了确保检索所有数据，应用程序必须继续调用 方法，`CInternetFile::Read`直到该方法返回零。

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>C互联网文件：：阅读字符串

调用此成员函数以读取字符流，直到它找到换行符。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>参数

*普斯特*<br/>
指向将接收正在读取的行的字符串的指针。

*nMax*<br/>
要读取的最大字符数。

*rString*<br/>
对接收读取行的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

指向从[CInternetFile](../../mfc/reference/cinternetfile-class.md)对象检索的普通数据的缓冲区的指针。 无论传递给此方法的缓冲区数据类型如何，它都会对数据执行任何操作（例如，转换为 Unicode），因此必须将返回的数据映射到预期的结构，就像返回**void**<strong>\*</strong>类型一样。

如果未读取任何数据就到达了文件结尾;或者，如果布尔，如果到达文件结尾而不读取任何数据。"

### <a name="remarks"></a>备注

函数将生成的行放入*pstr*参数引用的内存中。 当它达到*nMax*指定的字符的最大数量时，它将停止读取字符。 缓冲区始终接收终止空字符。

如果不首先调用`ReadString` [SetReadBufferSize，](#setreadbuffersize)则调用时将获得 4096 字节的缓冲区。

## <a name="cinternetfileseek"></a><a name="seek"></a>C 互联网文件：查找

调用此成员函数以重新定位以前打开的文件中的指针。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>参数

*l 偏移*<br/>
偏移以字节为单位，以移动文件中的读/写指针。

*n 从*<br/>
偏移的相对参照。 必须是以下值之一：

- `CFile::begin`从文件的开头向前移动文件指针*lOff*字节。

- `CFile::current`从文件中的当前位置移动文件指针*lOff*字节。

- `CFile::end`从文件末尾移动文件指针*lOff*字节。 *lOff*必须是负的才能查找到现有文件中;正值将查找文件末尾。

### <a name="return-value"></a>返回值

如果请求的位置是合法的，则从文件开头的新字节偏移量;否则，该值将未定义，并引发[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

### <a name="remarks"></a>备注

该`Seek`函数允许通过绝对或相对地将指针移动指定数量来随机访问文件的内容。 在查找过程中实际上不会读取任何数据。

此时，仅支持与`CHttpFile`对象关联的数据调用此成员函数。 FTP 或 gopher 请求不支持它。 如果您调用`Seek`这些不支持的服务之一，它将将您传回 Win32 错误代码ERROR_INTERNET_INVALID_OPERATION。

打开文件时，文件指针位于文件开头的偏移 0。

> [!NOTE]
> 使用`Seek`可能会导致隐式调用[Flush](#flush)。

### <a name="example"></a>示例

  请参阅基类实现的示例[（CFile：：seek](../../mfc/reference/cfile-class.md#seek)）。

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>C 互联网文件：：设置读取缓冲区大小

调用此成员函数以设置`CInternetFile`派生对象使用的临时读取缓冲区的大小。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>参数

*nReadSize*<br/>
所需的缓冲区大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

基础 WinInet API 不执行缓冲，因此请选择允许应用程序高效读取数据的缓冲区大小，而不考虑要读取的数据量。 如果每次对[Read](#read)的调用通常涉及大量数据（例如，四个或更多 KB），则不应需要缓冲区。 但是，如果您调用`Read`以获取小块数据，或者使用[ReadString](#readstring)一次读取单个行，则读取缓冲区可提高应用程序性能。

默认情况下，`CInternetFile`对象不提供任何用于读取的缓冲。 如果调用此成员函数，则必须确保该文件已打开以进行读取访问。

您可以随时增加缓冲区大小，但收缩缓冲区将不起作用。 如果调用[ReadString](#readstring)而不进行`SetReadBufferSize`第一次调用，您将获得 4096 字节的缓冲区。

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>C 互联网文件：：设置写入缓冲区大小

调用此成员函数以设置`CInternetFile`派生对象使用的临时写入缓冲区的大小。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>参数

*nWriteSize*<br/>
缓冲区的大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

基础 WinInet API 不执行缓冲，因此请选择允许应用程序高效写入数据的缓冲区大小，而不考虑要写入的数据量。 如果每次对[Write](#write)的调用通常涉及大量数据（例如，一次四个或更多千字节），则不应需要缓冲区。 但是，如果调用[Write](#write)来写入小块数据，则写入缓冲区会提高应用程序的性能。

默认情况下，`CInternetFile`对象不提供任何用于写入的缓冲。 如果调用此成员函数，则必须确保该文件已打开以进行写入访问。 您可以随时更改写入缓冲区的大小，但这样做会导致隐式调用[Flush](#flush)。

## <a name="cinternetfilewrite"></a><a name="write"></a>C互联网文件：写入

调用此成员函数写入给定的内存 *，lpvBuf，* 指定数量的字节 *，nCount*。

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

如果在写入数据时发生任何错误，该函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>C互联网文件：：写入字符串

此函数将一个 null 终止的字符串写入关联的文件。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>参数

*普斯特*<br/>
指向包含要写入内容的字符串的指针。

### <a name="remarks"></a>备注

如果在写入数据时发生任何错误，该函数将引发描述错误的[CInternetException](../../mfc/reference/cinternetexception-class.md)对象。

## <a name="see-also"></a>另请参阅

[CStdioFile 类](../../mfc/reference/cstdiofile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C 互联网连接类](../../mfc/reference/cinternetconnection-class.md)
