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
ms.openlocfilehash: f3d0be66bf0b5a6c07a72c8ae6cc9c90e176728f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167885"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 类

此类提供用于创建和使用临时文件的方法。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAtlTemporaryFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|构造函数。|
|[CAtlTemporaryFile：： ~ CAtlTemporaryFile](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlTemporaryFile：： Close](#close)|调用此方法可关闭临时文件，并删除其内容，或将其存储在指定的文件名下。|
|[CAtlTemporaryFile：： Create](#create)|调用此方法可创建临时文件。|
|[CAtlTemporaryFile：： Flush](#flush)|调用此方法可强制将文件缓冲区中剩余的所有数据写入临时文件。|
|[CAtlTemporaryFile::GetPosition](#getposition)|调用此方法以获取当前文件指针位置。|
|[CAtlTemporaryFile：： GetSize](#getsize)|调用此方法以获取临时文件的大小（以字节为单位）。|
|[CAtlTemporaryFile::HandsOff](#handsoff)|调用此方法可将文件与`CAtlTemporaryFile`对象解除关联。|
|[CAtlTemporaryFile::HandsOn](#handson)|调用此方法以打开现有的临时文件，并将指针放置在文件末尾。|
|[CAtlTemporaryFile::LockRange](#lockrange)|调用此方法可锁定文件中的某个区域，以防止其他进程对其进行访问。|
|[CAtlTemporaryFile：： Read](#read)|调用此方法以从文件指针指示的位置开始读取临时文件中的数据。|
|[CAtlTemporaryFile：： Seek](#seek)|调用此方法可移动临时文件的文件指针。|
|[CAtlTemporaryFile：： SetSize](#setsize)|调用此方法可设置临时文件的大小。|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|调用此方法以返回临时文件的名称。|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|调用此方法可对临时文件的区域进行解锁。|
|[CAtlTemporaryFile：： Write](#write)|调用此方法可将数据写入到从文件指针指示的位置开始的临时文件中。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlTemporaryFile：： operator 句柄](#operator_handle)|返回临时文件的句柄。|

## <a name="remarks"></a>备注

`CAtlTemporaryFile`可以轻松地创建和使用临时文件。 文件自动命名、打开、关闭和删除。 如果文件内容在文件关闭之后需要，则可以将其保存到具有指定名称的新文件。

## <a name="requirements"></a>要求

**标头：** atlfile

## <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

构造函数。

```cpp
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>备注

在调用[CAtlTemporaryFile：： Create](#create)之前，实际上不会打开文件。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile：： ~ CAtlTemporaryFile

析构函数。

```cpp
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>备注

析构函数调用[CAtlTemporaryFile：： Close](#close)。

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile：： Close

调用此方法可关闭临时文件，并删除其内容，或将其存储在指定的文件名下。

```cpp
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>参数

*szNewName*<br/>
用于存储临时文件的内容的新文件的名称。 如果此参数为 NULL，则删除临时文件的内容。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile：： Create

调用此方法可创建临时文件。

```cpp
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>参数

*pszDir*<br/>
临时文件的路径。 如果此值为 NULL，则将调用[GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)来分配一个路径。

*dwDesiredAccess*<br/>
所需的访问权限。 请参阅 Windows SDK 的[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)中的*dwDesiredAccess* 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile：： Flush

调用此方法可强制将文件缓冲区中剩余的所有数据写入临时文件。

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

类似于[CAtlTemporaryFile：： HandsOff](#handsoff)，但文件未关闭。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile::GetPosition

调用此方法以获取当前文件指针位置。

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
位置（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

若要更改文件指针位置，请使用[CAtlTemporaryFile：： Seek](#seek)。

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile：： GetSize

调用此方法以获取临时文件的大小（以字节为单位）。

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>参数

*nLen*<br/>
文件中的字节数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

调用此方法可将文件与`CAtlTemporaryFile`对象解除关联。

```cpp
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

`HandsOff`和[CAtlTemporaryFile：： HandsOn](#handson)用于取消该文件与对象的关联，并在需要时重新附加它。 `HandsOff`将强制将文件缓冲区中剩余的所有数据写入临时文件，然后关闭该文件。 如果要永久关闭并删除文件，或者要关闭并保留具有给定名称的文件内容，请使用[CAtlTemporaryFile：： close](#close)。

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

调用此方法以打开现有的临时文件，并将指针放置在文件末尾。

```cpp
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

[CAtlTemporaryFile：： HandsOff](#handsoff)和`HandsOn`用于断开文件与对象的关联，并在需要时将其重新附加。

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

调用此方法可锁定临时文件中的某个区域，以防止其他进程对其进行访问。

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
文件中应开始锁的位置。

*nCount*<br/>
要锁定的字节范围的长度。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。 若要成功解锁某个区域，请使用[CAtlTemporaryFile：： UnlockRange](#unlockrange)，确保字节范围与以前锁定的区域完全对应。 `LockRange`不合并相邻区域;如果两个锁定区域相邻，则必须单独解锁。

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile：： operator 句柄

返回临时文件的句柄。

```cpp
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile：： Read

调用此方法以从文件指针指示的位置开始读取临时文件中的数据。

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
指向缓冲区的指针，该缓冲区将接收从该文件中读取的数据。

*nBufSize*<br/>
缓冲区大小（以字节为单位）。

*nBytesRead*<br/>
已读取的字节数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：： Read](../../atl/reference/catlfile-class.md#read)。 若要更改文件指针的位置，请调用[CAtlTemporaryFile：： Seek](#seek)。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile：： Seek

调用此方法可移动临时文件的文件指针。

```cpp
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>参数

*nOffset*<br/>
DwFrom 指定的起始点的偏移量（以字节为单位） *。*

*dwFrom*<br/>
起始点（FILE_BEGIN、FILE_CURRENT 或 FILE_END）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：： Seek](../../atl/reference/catlfile-class.md#seek)。 若要获取当前文件指针位置，请调用[CAtlTemporaryFile：： GetPosition](#getposition)。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile：： SetSize

调用此方法可设置临时文件的大小。

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>参数

*nNewLen*<br/>
文件的新长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：： SetSize](../../atl/reference/catlfile-class.md#setsize)。 返回时，文件指针定位在文件的末尾。

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

调用此方法以返回临时文件的名称。

```cpp
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>返回值

返回指向文件名的 LPCTSTR。

### <a name="remarks"></a>备注

文件名在[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)中生成，并调用[GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)Windows SDK 函数。 对于临时文件，文件扩展名将始终为 "TFR"。

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

调用此方法可对临时文件的区域进行解锁。

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>参数

*nPos*<br/>
文件中应开始解除锁定的位置。

*nCount*<br/>
要解锁的字节范围的长度。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：： UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)。

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile：： Write

调用此方法可将数据写入到从文件指针指示的位置开始的临时文件中。

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
包含要写入到文件中的数据的缓冲区。

*nBufSize*<br/>
要从缓冲区传输的字节数。

*pnBytesWritten*<br/>
写入的字节数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CAtlFile：： Write](../../atl/reference/catlfile-class.md#write)。

### <a name="example"></a>示例

请参阅[CAtlTemporaryFile：： CAtlTemporaryFile](#catltemporaryfile)的示例。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CAtlFile 类](../../atl/reference/catlfile-class.md)
