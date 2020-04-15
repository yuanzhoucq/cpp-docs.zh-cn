---
title: CAtlTemporaryFile 类
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321310"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 类

此类提供创建和使用临时文件的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAtlTemporaryFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtl临时文件：CAtl临时文件](#catltemporaryfile)|构造函数。|
|[CAtl临时文件：*CAtl临时文件](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtl临时文件：关闭](#close)|调用此方法以关闭临时文件并删除其内容或将其存储在指定的文件名下。|
|[CAtl临时文件：创建](#create)|调用此方法以创建临时文件。|
|[CAtl临时文件：：Flush](#flush)|调用此方法以强制将文件缓冲区中剩余的任何数据写入临时文件。|
|[CAtl临时文件：获取位置](#getposition)|调用此方法获取当前文件指针位置。|
|[CAtl临时文件：获取Size](#getsize)|调用此方法以获取临时文件的大小（以字节为单位）。|
|[CAtl临时文件：：手关闭](#handsoff)|调用此方法以取消文件与对象关联的`CAtlTemporaryFile`文件。|
|[CAtl临时文件：：手](#handson)|调用此方法以打开现有临时文件并将指针放置在文件的末尾。|
|[CAtl临时文件：：锁定范围](#lockrange)|调用此方法以锁定文件中的区域，以防止其他进程访问它。|
|[CAtl 临时文件：阅读](#read)|调用此方法从临时文件读取从文件指针指示的位置开始的数据。|
|[CAtl临时文件：寻找](#seek)|调用此方法以移动临时文件的文件指针。|
|[CAtl 临时文件：：设置大小](#setsize)|调用此方法以设置临时文件的大小。|
|[CAtl临时文件：：圣殿文件名称](#tempfilename)|调用此方法以返回临时文件的名称。|
|[CAtl临时文件：：解锁范围](#unlockrange)|调用此方法以解锁临时文件的区域。|
|[CAtl临时文件：写入](#write)|调用此方法将数据写入从文件指针指示的位置开始的临时文件。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtl临时文件：：操作员HANDLE](#operator_handle)|返回临时文件的句柄。|

## <a name="remarks"></a>备注

`CAtlTemporaryFile`便于创建和使用临时文件。 该文件将自动命名、打开、关闭和删除。 如果在文件关闭后需要文件内容，则可以将文件内容保存到具有指定名称的新文件中。

## <a name="requirements"></a>要求

**标题：** atlfile.h

## <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtl临时文件：CAtl临时文件

构造函数。

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>备注

在调用[CAtlTemporaryFile：：：创建](#create)之前，文件实际上不会打开。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtl临时文件：*CAtl临时文件

析构函数。

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>备注

析构函数调用[CAtl临时文件：关闭](#close)。

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtl临时文件：关闭

调用此方法以关闭临时文件并删除其内容或将其存储在指定的文件名下。

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>参数

*szNewName*<br/>
用于将临时文件的内容存储在 其中的新文件的名称。 如果此参数为 NULL，则删除临时文件的内容。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtl临时文件：创建

调用此方法以创建临时文件。

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>参数

*皮兹迪尔*<br/>
临时文件的路径。 如果这是 NULL，则将调用[GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)来分配路径。

*dwddAccess*<br/>
所需的访问。 请参阅 Windows SDK 中的["创建文件](/windows/win32/api/fileapi/nf-fileapi-createfilew)"中的*dwdDAccess。*

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtl临时文件：：Flush

调用此方法以强制将文件缓冲区中剩余的任何数据写入临时文件。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

类似于[CAtl临时文件：：Handsoff，](#handsoff)只是文件未关闭。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtl临时文件：获取位置

调用此方法获取当前文件指针位置。

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
字节中的位置。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

要更改文件指针位置，请使用[CAtl临时文件：：查找](#seek)。

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtl临时文件：获取Size

调用此方法以获取临时文件的大小（以字节为单位）。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>参数

*nLen*<br/>
文件中的字节数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtl临时文件：：手关闭

调用此方法以取消文件与对象关联的`CAtlTemporaryFile`文件。

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

`HandsOff`和[CAtl临时文件：HandsOn](#handson)用于取消文件与对象关联的关联，并在需要时重新附加该文件。 `HandsOff`将强制将文件缓冲区中剩余的任何数据写入临时文件，然后关闭该文件。 如果要永久关闭和删除该文件，或者要关闭和保留具有给定名称的文件的内容，请使用[CAtlTemporaryFile：：关闭](#close)。

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtl临时文件：：手

调用此方法以打开现有临时文件并将指针放置在文件的末尾。

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CAtl临时文件：：HandsOff，](#handsoff)`HandsOn`用于取消文件与对象的关联，并在需要时重新附加它。

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtl临时文件：：锁定范围

调用此方法以锁定临时文件中的区域，以防止其他进程访问它。

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
锁应开始的文件中的位置。

*nCount*<br/>
要锁定的字节范围的长度。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。 要成功解锁区域，请使用[CAtlTemporaryFile：：unlockRange，](#unlockrange)确保字节范围与以前锁定的区域完全对应。 `LockRange`不合并相邻区域;不合并相邻区域。如果两个锁定区域相邻，则必须单独解锁每个区域。

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtl临时文件：：操作员HANDLE

返回临时文件的句柄。

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtl 临时文件：阅读

调用此方法从临时文件读取从文件指针指示的位置开始的数据。

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
指向将接收从文件读取的数据的缓冲区的指针。

*nBufSize*<br/>
缓冲区大小（以字节为单位）。

*n 字节读取*<br/>
已读取的字节数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：读取](../../atl/reference/catlfile-class.md#read)。 要更改文件指针的位置，请致电[CAtlTemporaryFile：：seek](#seek)。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtl临时文件：寻找

调用此方法以移动临时文件的文件指针。

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>参数

*n偏移*<br/>
从*dwFrom*给出的起始点偏移（以字节为单位）。

*dwfrom*<br/>
起点（FILE_BEGIN、FILE_CURRENT或FILE_END）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：：查找](../../atl/reference/catlfile-class.md#seek)。 要获取当前文件指针位置，请致电[CAtl临时文件：：get定位](#getposition)。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtl 临时文件：：设置大小

调用此方法以设置临时文件的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>参数

*n 纽伦*<br/>
文件的新长度（以字节为单位）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：：设置大小](../../atl/reference/catlfile-class.md#setsize)。 返回时，文件指针位于文件的末尾。

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtl临时文件：：圣殿文件名称

调用此方法以返回临时文件的名称。

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>返回值

返回指向文件名的 LPCTSTR。

### <a name="remarks"></a>备注

文件名在[CAtl临时文件：：CAtl临时文件](#catltemporaryfile)与访问[GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 功能时生成。 临时文件的文件扩展名将始终为"TFR"。

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtl临时文件：：解锁范围

调用此方法以解锁临时文件的区域。

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
应开始解锁的文件中的位置。

*nCount*<br/>
要解锁的字节范围的长度。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：解锁范围](../../atl/reference/catlfile-class.md#unlockrange)。

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtl临时文件：写入

调用此方法将数据写入从文件指针指示的位置开始的临时文件。

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
包含要写入文件的数据的缓冲区。

*nBufSize*<br/>
要从缓冲区传输的字节数。

*pn字节写入*<br/>
写入的字节数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：写入](../../atl/reference/catlfile-class.md#write)。

### <a name="example"></a>示例

请参阅[CAtl临时文件的示例：CAtl临时文件](#catltemporaryfile)。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CAtlFile 类](../../atl/reference/catlfile-class.md)
