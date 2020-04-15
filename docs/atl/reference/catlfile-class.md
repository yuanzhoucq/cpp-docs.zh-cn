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
ms.openlocfilehash: 39f323874ccde5178722235b9beb34c2572407a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318966"
---
# <a name="catlfile-class"></a>CAtlFile 类

此类在 Windows 文件处理 API 周围提供一个精简包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAtlFile : public CHandle
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlFile：CAtlFile](#catlfile)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlFile：创建](#create)|调用此方法以创建或打开文件。|
|[CAtlFile：冲洗](#flush)|调用此方法以清除文件的缓冲区，并导致将所有缓冲数据写入该文件。|
|[CAtlFile：获取重叠结果](#getoverlappedresult)|调用此方法以获取文件上重叠操作的结果。|
|[CAtlFile：获取位置](#getposition)|调用此方法从文件中获取当前文件指针位置。|
|[CAtlFile：获取 Size](#getsize)|调用此方法以获取文件的大小（以字节为单位）。|
|[CAtlFile：锁定范围](#lockrange)|调用此方法以锁定文件中的区域，以防止其他进程访问它。|
|[CAtlFile：阅读](#read)|调用此方法从文件读取数据，从文件指针指示的位置开始。|
|[CAtlFile：寻找](#seek)|调用此方法以移动文件的文件指针。|
|[CAtlFile：设置大小](#setsize)|调用此方法以设置文件的大小。|
|[CAtlFile：解锁范围](#unlockrange)|调用此方法以解锁文件的区域。|
|[CAtlFile：写入](#write)|调用此方法将数据写入文件，从文件指针指示的位置开始。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CAtlFile：m_pTM](#m_ptm)|指向`CAtlTransactionManager`对象的指针|

## <a name="remarks"></a>备注

当文件处理需求相对简单，但需要比 Windows API 提供的更多的抽象，但不包括 MFC 依赖项时，请使用此类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[手柄](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>要求

**标题：** atlfile.h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile：CAtlFile

构造函数。

```
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

复制构造函数将文件句柄的所有权从原始`CAtlFile`对象转移到新构造的对象。

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile：创建

调用此方法以创建或打开文件。

```
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

*dwddAccess*<br/>
所需的访问。 请参阅 Windows SDK 中的["创建文件](/windows/win32/api/fileapi/nf-fileapi-createfilew)"中的*dwdDAccess。*

*dwShareMode*<br/>
共享模式。 请参阅 中的`CreateFile` *dwShareMode。*

*德沃创意*<br/>
创建处置。 请参阅 中的`CreateFile` *dw 创造处理。*

*dwflags 和属性*<br/>
标志和属性。 请参阅 中的`CreateFile` *dwFlags 和属性*。

*lpsa*<br/>
安全属性。 请参阅 中的`CreateFile` *lpSecurity 属性*。

*h模板文件*<br/>
模板文件。 请参阅 中的`CreateFile` *hTemplateFile。*

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)创建或打开文件。

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile：冲洗

调用此方法以清除文件的缓冲区，并导致将所有缓冲数据写入该文件。

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[FlushFileBuffer 以](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers)刷新缓冲的数据到文件。

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile：获取重叠结果

调用此方法以获取文件上重叠操作的结果。

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>参数

*p重叠*<br/>
重叠的结构。 在 Windows SDK 中查看 *"重叠*[结果](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)"。

*dwBytes 传输*<br/>
传输的字节数。 请参阅 在 中`GetOverlappedResult`*传输的 lp 编号数*。

*b 等待*<br/>
等待选项。 请参阅*b* `GetOverlappedResult`等待。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult)获取文件上重叠操作的结果。

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile：获取位置

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

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)获取当前文件指针位置。

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile：获取 Size

调用此方法以获取文件的大小（以字节为单位）。

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>参数

*nLen*<br/>
文件中的字节数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize)以获取文件的大小（以字节为单位）。

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile：锁定范围

调用此方法以锁定文件中的区域，以防止其他进程访问它。

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

调用[LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile)以锁定文件中的区域。 锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。 当您解锁区域时，使用[CAtlFile：：unlockRange，](#unlockrange)字节范围必须与以前锁定的区域完全对应。 `LockRange`不合并相邻区域;不合并相邻区域。如果两个锁定区域相邻，则必须单独解锁每个区域。

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile：m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

## <a name="catlfileread"></a><a name="read"></a>CAtlFile：阅读

调用此方法从文件读取数据，从文件指针指示的位置开始。

```
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
指向将接收从文件读取的数据的缓冲区的指针。

*nBufSize*<br/>
缓冲区大小（以字节为单位）。

*n 字节读取*<br/>
已读取的字节数。

*p重叠*<br/>
重叠的结构。 在 Windows SDK 中的["读取文件](/windows/win32/api/fileapi/nf-fileapi-readfile)"中查看*lp 重叠*。

*pfn 完成例程*<br/>
完成例程。 请参阅 Windows SDK 中的["阅读文件更新](/windows/win32/api/fileapi/nf-fileapi-readfileex)"中的*lp 完成例程*。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[ReadFile，](/windows/win32/api/fileapi/nf-fileapi-readfile)这是最后一个从文件读取数据的[ReadFileEx。](/windows/win32/api/fileapi/nf-fileapi-readfileex) 使用[CAtlFile：：寻求](#seek)移动文件指针。

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile：寻找

调用此方法以移动文件的文件指针。

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>参数

*n偏移*<br/>
dwFrom 给出的起始点的偏移*dwFrom*量。

*dwfrom*<br/>
起点（FILE_BEGIN、FILE_CURRENT或FILE_END）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)以移动文件指针。

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile：设置大小

调用此方法以设置文件的大小。

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>参数

*n 纽伦*<br/>
文件的新长度（以字节为单位）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer)和[SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile)来设置文件的大小。 返回时，文件指针位于文件的末尾。

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile：解锁范围

调用此方法以解锁文件的区域。

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

调用[解锁文件](/windows/win32/api/fileapi/nf-fileapi-unlockfile)以解锁文件的区域。

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile：写入

调用此方法将数据写入文件，从文件指针指示的位置开始。

```
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
包含要写入文件的数据的缓冲区。

*nBufSize*<br/>
要从缓冲区传输的字节数。

*p重叠*<br/>
重叠的结构。 在 Windows SDK 中的[写入文件](/windows/win32/api/fileapi/nf-fileapi-writefile)中查看*lp 重叠*。

*pfn 完成例程*<br/>
完成例程。 请参阅 Windows SDK 中的[写入文件Ex](/windows/win32/api/fileapi/nf-fileapi-writefileex)中的*lp 完成例程*。

*pn字节写入*<br/>
写入的字节。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

前三个窗体调用[WriteFile，](/windows/win32/api/fileapi/nf-fileapi-writefile)最后调用[WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex)将数据写入文件。 使用[CAtlFile：：寻求](#seek)移动文件指针。

## <a name="see-also"></a>另请参阅

[选框示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CHandle 类](../../atl/reference/chandle-class.md)
