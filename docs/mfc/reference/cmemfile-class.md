---
title: CMemFile 类
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: a57f4e245ca1e93ec0edd454a7f407aeda5beca4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304933"
---
# <a name="cmemfile-class"></a>CMemFile 类

[CFile](../../mfc/reference/cfile-class.md)-派生的类支持内存文件。

## <a name="syntax"></a>语法

```
class CMemFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|构造一个内存文件对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMemFile::Attach](#attach)|将附加到的内存块`CMemFile`。|
|[CMemFile::Detach](#detach)|分离中的内存块`CMemFile`并返回到分离的内存块的指针。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|重写以修改内存分配行为。|
|[CMemFile::Free](#free)|重写以修改内存释放行为。|
|[CMemFile::GrowFile](#growfile)|重写以增大文件时修改行为。|
|[CMemFile::Memcpy](#memcpy)|重写以修改内存复制行为时读取和写入文件。|
|[CMemFile::Realloc](#realloc)|重写以修改内存重新分配行为。|

## <a name="remarks"></a>备注

这些内存文件类似于磁盘文件的不同是该文件存储在 RAM 中，而不是磁盘上。 对于快速临时存储，或者传输原始字节或序列化的对象之间独立进程内存文件。

`CMemFile` 对象可以自动将它们自己的内存分配，也可以附加到你自己的内存块`CMemFile`对象通过调用[附加](#attach)。 在任一情况下，自动增大内存文件的内存分配中`nGrowBytes`-如果大小为增量`nGrowBytes`不为零。

析构时将自动被删除的内存块`CMemFile`对象通过了最初在分配内存`CMemFile`对象; 否则，您还要负责释放附加到对象的内存。

您可以通过提供从分离时的指针访问内存块`CMemFile`对象通过调用[分离](#detach)。

最常见用法`CMemFile`是创建`CMemFile`对象并使用它通过调用[CFile](../../mfc/reference/cfile-class.md)成员函数。 请注意，创建`CMemFile`会自动打开它： 不调用[CFile::Open](../../mfc/reference/cfile-class.md#open)，这仅用于磁盘文件。 因为`CMemFile`不使用磁盘文件，数据成员`CFile::m_hFile`不使用。

`CFile`成员函数[重复](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，并且[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)未实现的`CMemFile`。 如果你对调用这些函数`CMemFile`对象，则将会出现[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile` 使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)， [realloc](../../c-runtime-library/reference/realloc.md)，并[免费](../../c-runtime-library/reference/free.md)分配，重新分配和解除分配内存; 并且该内部函数[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)读取和写入时的内存块复制。 如果想要更改此行为或行为时`CMemFile`增长文件派生您自己的类从`CMemFile`和重写适当的函数。

有关详细信息`CMemFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)并[内存管理 (MFC)](../../mfc/memory-management.md) ，并查看[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

调用此函数`CMemFile`成员函数。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*nBytes*<br/>
要分配的内存字节数。

### <a name="return-value"></a>返回值

指向已分配的内存块的指针或 NULL，如果分配失败。

### <a name="remarks"></a>备注

重写此函数可实现自定义内存分配。 如果重写此函数，您可能需要重写[免费](#free)并[Realloc](#realloc)也。

默认实现使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)来分配内存。

##  <a name="attach"></a>  CMemFile::Attach

调用此函数可将附加到的内存块`CMemFile`。

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*lpBuffer*<br/>
要附加到的缓冲区的指针`CMemFile`。

*nBufferSize*<br/>
一个整数，指定缓冲区的大小以字节为单位。

*nGrowBytes*<br/>
内存分配的增量以字节为单位。

### <a name="remarks"></a>备注

这将导致`CMemFile`为内存文件中使用的内存块。

如果*nGrowBytes*为 0，`CMemFile`会将文件长度设置为*nBufferSize*。 这意味着，内存块中的数据之前已附加到`CMemFile`将用作该文件。 不能增长以这种方式创建的内存文件。

由于该文件无法增长，请注意不要导致`CMemFile`尝试增长的文件。 例如，不要调用`CMemFile`的重写[CFile:Write](../../mfc/reference/cfile-class.md#write)到末尾写入或不调用[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)使用的长度超过*nBufferSize*。

如果*nGrowBytes*大于 0，`CMemFile`将忽略已附加的内存块的内容。 您必须编写从从头开始使用的内存文件的内容`CMemFile`重写的`CFile::Write`。 如果你尝试在文件末尾写入或通过调用增长的文件`CMemFile`的重写`CFile::SetLength`，`CMemFile`将会增长增量为内存分配*nGrowBytes*。 如果内存块将传递给不断增长的内存分配将失败`Attach`不使用与兼容的方法分配[Alloc](#alloc)。 若要使用的默认实现兼容`Alloc`，您必须分配与运行时库函数的内存[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)。

##  <a name="cmemfile"></a>  CMemFile::CMemFile

第一个重载将打开一个空的内存文件中。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*nGrowBytes*<br/>
内存分配的增量以字节为单位。

*lpBuffe*r 指针指向接收信息的大小的缓冲区*nBufferSize*。

*nBufferSize*<br/>
一个整数，以字节为单位指定文件缓冲区的大小。

### <a name="remarks"></a>备注

请注意由构造函数打开该文件，并且您不应调用[CFile::Open](../../mfc/reference/cfile-class.md#open)。

第二个重载看起来相同就像在使用了第一个构造函数并立即调用[附加](#attach)使用相同的参数。 有关详细信息，请参阅`Attach`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

调用此函数可获取到正在使用的内存块的指针`CMemFile`。

```
BYTE* Detach();
```

### <a name="return-value"></a>返回值

指向包含内存文件的内容的内存块的指针。

### <a name="remarks"></a>备注

调用此函数还将关闭`CMemFile`。 您可以重新附加到的内存块`CMemFile`通过调用[附加](#attach)。 如果你想要重新附加该文件并在其中使用的数据，则应调用[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength)若要获取长度的文件，然后再调用`Detach`。 请注意，如果附加到的内存块`CMemFile`，以便可以使用其数据 ( `nGrowBytes` = = 0)，则会有增长的内存文件。

##  <a name="free"></a>  CMemFile::Free

调用此函数`CMemFile`成员函数。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指向要释放的内存的指针。

### <a name="remarks"></a>备注

重写此函数可实现自定义内存释放。 如果重写此函数，您可能需要重写[Alloc](#alloc)并[Realloc](#realloc)也。

##  <a name="growfile"></a>  CMemFile::GrowFile

此函数调用由几个`CMemFile`成员函数。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>参数

*dwNewLen*<br/>
新的内存文件的大小。

### <a name="remarks"></a>备注

如果你想要更改可以覆盖它如何`CMemFile`其文件的增长。 默认实现调用[Realloc](#realloc)增长的现有块 (或[Alloc](#alloc)若要创建的内存块)，分配内存的倍数`nGrowBytes`构造函数中指定的值或[附加](#attach)调用。

##  <a name="memcpy"></a>  CMemFile::Memcpy

调用此函数`CMemFile`重写[CFile::Read](../../mfc/reference/cfile-class.md#read)并[CFile::Write](../../mfc/reference/cfile-class.md#write)传输数据传入和传出的内存文件。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMemTarget*<br/>
将向其中复制源内存的内存块的指针。

*lpMemSource*<br/>
指向源内存块的指针。

*nBytes*<br/>
要复制的字节数。

### <a name="return-value"></a>返回值

一份*lpMemTarget*。

### <a name="remarks"></a>备注

如果你想要更改的方式重写此函数的`CMemFile`does 这些内存副本。

##  <a name="realloc"></a>  CMemFile::Realloc

调用此函数`CMemFile`成员函数。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指向要重新分配的内存块的指针。

*nBytes*<br/>
新的内存块的大小。

### <a name="return-value"></a>返回值

指向内存块已重新分配 （并且可能是移动），或如果在重新分配失败，则为 NULL。

### <a name="remarks"></a>备注

重写此函数可实现自定义内存重新分配。 如果重写此函数，您可能需要重写[Alloc](#alloc)并[免费](#free)也。

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
