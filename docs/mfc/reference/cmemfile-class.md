---
title: CMemFile 类
description: 介绍 CMemFile 类中提供的可用于处理内存文件的函数。
ms.date: 07/23/2020
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CmemFile::GetBufferPtr
- AFX/CMemFile::GrowFile"
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GetBufferPtr
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: edd1d8b8d3979427602bdb61fc7647aec15d58b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222935"
---
# <a name="cmemfile-class"></a>CMemFile 类

支持内存文件的[CFile](../../mfc/reference/cfile-class.md)派生类。

## <a name="syntax"></a>语法

```
class CMemFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMemFile：： CMemFile](#cmemfile)|构造内存文件对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CMemFile：： Attach](#attach)|将内存块附加到 `CMemFile` 。|
|[CMemFile：:D etach](#detach)|从分离内存块 `CMemFile` ，并返回指向已分离内存块的指针。|
|[CMemFile：： GetBufferPtr](#getbufferptr)|获取或写入用于支持内存文件的内存缓冲区。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMemFile：：分配](#alloc)|重写以修改内存分配行为。|
|[CMemFile：： Free](#free)|重写以修改内存释放行为。|
|[CMemFile：： GrowFile](#growfile)|重写以在增大文件时修改行为。|
|[CMemFile：： Memcpy](#memcpy)|重写以修改读取和写入文件时的内存复制行为。|
|[CMemFile：： Realloc](#realloc)|重写以修改内存重新分配行为。|

## <a name="remarks"></a>备注

这些内存文件的行为类似于磁盘文件，但文件存储在 RAM 中，而不是存储在磁盘上。 内存文件适用于：

- 快速临时存储
- 在独立进程之间传输原始字节
- 在独立进程之间传输序列化对象

`CMemFile`对象可以自动分配其自己的内存。 或者，可以通过调用 Attach 将自己的内存块附加到 `CMemFile` 对象[Attach](#attach)。 在这两种情况下，如果不是零，则会按大小增加自动分配内存文件的内存 `nGrowBytes` `nGrowBytes` 。

如果对象最初由对象分配，则内存块将在对象被销毁时自动删除 `CMemFile` `CMemFile` ; 否则，您需要负责释放附加到对象的内存。

通过调用分离，可以通过在从对象分离时提供的指针访问内存块 `CMemFile` 。 [Detach](#detach)

最常见的用途 `CMemFile` 是 `CMemFile` 通过调用[CFile](../../mfc/reference/cfile-class.md)成员函数来创建对象并使用该对象。 创建 `CMemFile` 会自动打开它：不会调用[CFile：： Open](../../mfc/reference/cfile-class.md#open)，后者仅用于磁盘文件。 由于 `CMemFile` 不使用磁盘文件，因此 `CFile::m_hFile` 不使用数据成员。

`CFile`不会为[Duplicate](../../mfc/reference/cfile-class.md#duplicate)实现成员函数[LockRange](../../mfc/reference/cfile-class.md#lockrange)和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) `CMemFile` 。 如果在对象上调用这些函数 `CMemFile` ，将获得一个[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile`使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和[free](../../c-runtime-library/reference/free.md) ，以分配、重新分配和释放内存;在读取和写入时，用于阻止复制内存的内部[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) 。 如果要更改此行为或增长文件时的行为 `CMemFile` ，请从派生您自己的类， `CMemFile` 并重写相应的函数。

有关的详细信息 `CMemFile` ，请参阅文章[Mfc](../../mfc/files-in-mfc.md)和[内存管理（Mfc）](../../mfc/memory-management.md)中的文件和*运行时库参考*中的[文件处理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile：：分配

此函数由 `CMemFile` 成员函数调用。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*nBytes*<br/>
要分配的内存字节数。

### <a name="return-value"></a>返回值

指向已分配内存块的指针; 如果分配失败，则为 NULL。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存分配。 如果重写此函数，则可能还需要覆盖[Free](#free)和[Realloc](#realloc) 。

默认实现使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)来分配内存。

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile：： Attach

调用此函数可将内存块附加到 `CMemFile` 。

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*lpBuffer*<br/>
指向要附加到的缓冲区的指针 `CMemFile` 。

*nBufferSize*<br/>
一个整数，指定缓冲区的大小（以字节为单位）。

*nGrowBytes*<br/>
内存分配递增量（以字节为单位）。

### <a name="remarks"></a>备注

这会导致 `CMemFile` 使用内存块作为内存文件。

如果*nGrowBytes*为0， `CMemFile` 则将文件长度设置为*nBufferSize*。 这意味着，在附加到之前，内存块中的数据 `CMemFile` 将用作该文件。 无法增加以这种方式创建的内存文件。

由于文件无法增长，因此请注意不要导致 `CMemFile` 尝试增长文件。 例如，请不要调用 `CMemFile` [CFile： write](../../mfc/reference/cfile-class.md#write)的替代以写入结束，或不要调用长度超过*NBufferSize*的[CFile： SetLength](../../mfc/reference/cfile-class.md#setlength) 。

如果*nGrowBytes*大于0， `CMemFile` 将忽略附加的内存块的内容。 您必须使用的替代从头开始编写内存文件的内容 `CMemFile` `CFile::Write` 。 如果尝试写入超过文件末尾的文件或通过调用的重写来增长文件 `CMemFile` `CFile::SetLength` ， `CMemFile` 则将以*nGrowBytes*的增量增长内存分配。 如果传递到的内存块未 `Attach` 使用与[分配](#alloc)兼容的方法进行分配，则增大内存分配将会失败。 若要与的默认实现兼容 `Alloc` ，必须用运行库函数[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)分配内存。

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile：： CMemFile

第一个重载打开空内存文件。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*nGrowBytes*<br/>
内存分配递增量（以字节为单位）。

*lpBuffer*指向缓冲区的指针，该缓冲区接收大小*nBufferSize*的信息。

*nBufferSize*<br/>
一个整数，指定文件缓冲区的大小（以字节为单位）。

### <a name="remarks"></a>备注

该文件由构造函数打开。 请勿调用[CFile：： Open](../../mfc/reference/cfile-class.md#open)。

第二个重载的行为与使用第一个构造函数并立即调用具有相同参数的[Attach](#attach)相同。 有关详细信息，请参阅`Attach`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile：:D etach

调用此函数可获取指向正在使用的内存块的指针 `CMemFile` 。

```
BYTE* Detach();
```

### <a name="return-value"></a>返回值

指向包含内存文件内容的内存块的指针。

### <a name="remarks"></a>备注

调用此函数也会关闭 `CMemFile` 。 可以 `CMemFile` 通过调用[Attach](#attach)将内存块重新附加到。 如果要重新附加文件并使用其中的数据，则应调用[CFile：： GetLength](../../mfc/reference/cfile-class.md#getlength)以获取文件的长度，然后再调用 `Detach` 。 如果将内存块附加到， `CMemFile` 以便可以使用其数据（ `nGrowBytes` = = 0），则不能增加内存文件。

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile：： Free

此函数由 `CMemFile` 成员函数调用。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指向要释放的内存的指针。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存释放。 如果重写此函数，则可能还需要重写[分配](#alloc)和[Realloc](#realloc) 。

## <a name="cmemfilegetbufferptr"></a><a name="getbufferptr"></a>CMemFile：： GetBufferPtr

获取或写入用于支持内存文件的内存缓冲区。

```cpp
virtual UINT GetBufferPtr(
    UINT nCommand,
    UINT nCount = 0,
    void** ppBufStart = NULL,
    void** ppBufMax = NULL
);
```

### <a name="parameters"></a>参数

*N 命令*<br/>
要执行的[bufferCommand](buffercommand-enumeration.md) （ `bufferCheck` 、 `bufferCommit` 、 `bufferRead` 或 `bufferWrite` ）。

*nCount*<br/>
根据*n 命令*，为读取、写入或提交的缓冲区中的字节数。 从缓冲区中读取时，指定-1 将从当前位置到文件末尾返回缓冲区。

*ppBufStart*<br/>
弄缓冲区的开头。 `NULL`当*n 命令*为时，必须为 `bufferCommit` 。

*ppBufMax*<br/>
弄缓冲区的末尾。 `NULL`当 n 命令为时，必须为 `bufferCommit` 。

### <a name="return-value"></a>返回值

| *命令*值 | 返回值 |
|--|--|
| `buffercheck` | 如果支持直接缓冲，则返回[bufferDirect](buffercommand-enumeration.md) ，否则返回0。 |
| `bufferCommit` | 返回 `0` |
| `bufferRead` 或 `bufferWrite` | 返回返回的缓冲区空间中的字节数。 *ppBufStart*和*ppBufMax*指向读取/写入缓冲区的开头和结尾。  |

### <a name="remarks"></a>备注

内存缓冲区（）中的当前位置 `m_nPosition` 是高级的，具体取决于*n 命令*：

| *N 命令* | 缓冲区位置 |
|-|-|
| `bufferCommit` | 当前位置按提交的缓冲区的大小前进。 |
| `bufferRead` | 当前位置按读取缓冲区的大小前进。 |

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile：： GrowFile

此函数由若干个 `CMemFile` 成员函数调用。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>参数

*dwNewLen*<br/>
内存文件的新大小。

### <a name="remarks"></a>备注

如果要更改其文件的增长方式，可以重写它 `CMemFile` 。 默认实现将调用[Realloc](#realloc)来扩大现有块（或[分配](#alloc)到创建内存块），并以 `nGrowBytes` 构造函数中指定的值的倍数分配内存或[附加](#attach)调用。

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile：： Memcpy

此函数由 `CMemFile` [CFile：： Read](../../mfc/reference/cfile-class.md#read)和[CFile：： Write](../../mfc/reference/cfile-class.md#write)的重写调用，以将数据传入和传出内存文件。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMemTarget*<br/>
指向源内存要复制到的内存块的指针。

*lpMemSource*<br/>
指向源内存块的指针。

*nBytes*<br/>
要复制的字节数。

### <a name="return-value"></a>返回值

*LpMemTarget*的副本。

### <a name="remarks"></a>备注

如果要更改 `CMemFile` 执行这些内存复制的方式，请重写此函数。

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile：： Realloc

此函数由 `CMemFile` 成员函数调用。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指向要重新分配的内存块的指针。

*nBytes*<br/>
内存块的新大小。

### <a name="return-value"></a>返回值

指向内存块的指针，该内存块已重新分配（并且可能已移动），如果重新分配失败，则为 NULL。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存重新分配。 如果重写此函数，则可能还需要重写[分配](#alloc)和[免费](#free)。

## <a name="see-also"></a>另请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
