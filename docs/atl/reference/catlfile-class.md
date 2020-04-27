---
title: CAtlFile 类
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 83a0a89bf6e2e21be33cf8c6003228111eff5394
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168106"
---
# <a name="catlfile-class"></a>CAtlFile 类

此类提供了围绕 Windows 文件处理 API 的精简包装器。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAtlFile : public CHandle
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlFile：： Create](#create)|调用此方法可创建或打开文件。|
|[CAtlFile：： Flush](#flush)|调用此方法可清除文件缓冲区，并使所有缓冲的数据都写入到文件中。|
|[CAtlFile：： Getoverlappedresult 期间](#getoverlappedresult)|调用此方法可获取对文件的重叠操作的结果。|
|[CAtlFile::GetPosition](#getposition)|调用此方法可从文件获取当前文件指针位置。|
|[CAtlFile：： GetSize](#getsize)|调用此方法以获取文件的大小（以字节为单位）。|
|[CAtlFile::LockRange](#lockrange)|调用此方法可锁定文件中的某个区域，以防止其他进程对其进行访问。|
|[CAtlFile：： Read](#read)|调用此方法可从文件指针指示的位置开始读取文件中的数据。|
|[CAtlFile：： Seek](#seek)|调用此方法来移动文件的文件指针。|
|[CAtlFile：： SetSize](#setsize)|调用此方法设置文件的大小。|
|[CAtlFile::UnlockRange](#unlockrange)|调用此方法可以解锁文件区域。|
|[CAtlFile：： Write](#write)|调用此方法可将数据写入到文件指针所指示位置处的文件。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CAtlFile：： m_pTM](#m_ptm)|指向对象`CAtlTransactionManager`的指针|

## <a name="remarks"></a>备注

如果文件处理需求相对简单，但需要比 Windows API 提供的更多抽象，而不包括 MFC 依赖项，请使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>要求

**标头：** atlfile

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

构造函数。

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>参数

*文件*<br/>
文件对象。

*hFile*<br/>
文件句柄。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

复制构造函数将文件句柄的所有权从原始`CAtlFile`对象传输到新构造的对象。

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile：： Create

调用此方法可创建或打开文件。

```cpp
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>参数

*szFilename*<br/>
文件名。

*dwDesiredAccess*<br/>
所需的访问权限。 请参阅 Windows SDK 的[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)中的*dwDesiredAccess* 。

*dwShareMode*<br/>
共享模式。 请*dwShareMode*参阅中`CreateFile`的 dwShareMode。

*dwCreationDisposition*<br/>
创建处置。 请*dwCreationDisposition*参阅中`CreateFile`的 dwCreationDisposition。

*dwFlagsAndAttributes*<br/>
标志和特性。 请*dwFlagsAndAttributes*参阅中`CreateFile`的 dwFlagsAndAttributes。

*lpsa*<br/>
安全特性。 请*lpSecurityAttributes*参阅中`CreateFile`的 lpSecurityAttributes。

*hTemplateFile*<br/>
模板文件。 请*hTemplateFile*参阅中`CreateFile`的 hTemplateFile。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)创建或打开该文件。

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile：： Flush

调用此方法可清除文件缓冲区，并使所有缓冲的数据都写入到文件中。

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers)将缓冲的数据刷新到该文件。

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile：： Getoverlappedresult 期间

调用此方法可获取对文件的重叠操作的结果。

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>参数

*pOverlapped*<br/>
重叠的结构。 请参阅 Windows SDK 的[getoverlappedresult 期间](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)中的*lpOverlapped* 。

*dwBytesTransferred*<br/>
传输的字节数。 请*lpNumberOfBytesTransferred*参阅中`GetOverlappedResult`的 lpNumberOfBytesTransferred。

*bWait*<br/>
Wait 选项。 请*bWait*参阅中`GetOverlappedResult`的 bWait。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[getoverlappedresult 期间](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)以获取文件的重叠操作的结果。

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile::GetPosition

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

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)以获取当前文件指针位置。

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile：： GetSize

调用此方法以获取文件的大小（以字节为单位）。

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>参数

*nLen*<br/>
文件中的字节数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize)以获取文件的大小（以字节为单位）。

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

调用此方法可锁定文件中的某个区域，以防止其他进程对其进行访问。

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

调用[LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile)锁定文件中的区域。 锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。 使用[CAtlFile：： UnlockRange](#unlockrange)解锁某个区域时，字节范围必须完全与以前锁定的区域相对应。 `LockRange`不合并相邻区域;如果两个锁定区域相邻，则必须单独解锁。

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile：： m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

## <a name="catlfileread"></a><a name="read"></a>CAtlFile：： Read

调用此方法可从文件指针指示的位置开始读取文件中的数据。

```cpp
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
指向缓冲区的指针，该缓冲区将接收从该文件中读取的数据。

*nBufSize*<br/>
缓冲区大小（以字节为单位）。

*nBytesRead*<br/>
已读取的字节数。

*pOverlapped*<br/>
重叠的结构。 请参阅 Windows SDK 的[ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)中的*lpOverlapped* 。

*pfnCompletionRoutine*<br/>
完成例程。 请参阅 Windows SDK 的[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)中的*lpCompletionRoutine* 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile)，最后一个[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)从文件中读取数据。 使用[CAtlFile：： Seek](#seek)移动文件指针。

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile：： Seek

调用此方法来移动文件的文件指针。

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>参数

*nOffset*<br/>
*DwFrom*指定的起始点的偏移量。

*dwFrom*<br/>
起始点（FILE_BEGIN、FILE_CURRENT 或 FILE_END）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)移动文件指针。

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile：： SetSize

调用此方法设置文件的大小。

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>参数

*nNewLen*<br/>
文件的新长度（以字节为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)和[SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile)来设置文件的大小。 返回时，文件指针定位在文件的末尾。

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

调用此方法可以解锁文件区域。

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

调用[UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile)来解锁文件区域。

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile：： Write

调用此方法可将数据写入到文件指针所指示位置处的文件。

```cpp
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>参数

*pBuffer*<br/>
包含要写入到文件中的数据的缓冲区。

*nBufSize*<br/>
要从缓冲区传输的字节数。

*pOverlapped*<br/>
重叠的结构。 请参阅 Windows SDK 的[WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)中的*lpOverlapped* 。

*pfnCompletionRoutine*<br/>
完成例程。 请参阅 Windows SDK 的[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)中的*lpCompletionRoutine* 。

*pnBytesWritten*<br/>
写入的字节数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile)，最后调用[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)将数据写入文件。 使用[CAtlFile：： Seek](#seek)移动文件指针。

## <a name="see-also"></a>另请参阅

[天棚示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CHandle 类](../../atl/reference/chandle-class.md)
