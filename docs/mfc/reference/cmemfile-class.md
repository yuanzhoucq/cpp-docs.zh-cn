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
ms.openlocfilehash: 1bd88ad17bdb047de4c344ab96f3d9aecbe23c31
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752636"
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
|[CMem文件：CMemFile](#cmemfile)|构造内存文件对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMem文件：附加](#attach)|将内存块附加到`CMemFile`。|
|[CMemFile：:D](#detach)|从分离内存块`CMemFile`并返回指向分离的内存块的指针。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMemFile：Alloc](#alloc)|重写以修改内存分配行为。|
|[CMemFile：免费](#free)|重写以修改内存处理行为。|
|[CMemFile：：增长文件](#growfile)|在增长文件时重写以修改行为。|
|[CMemFile：Memcpy](#memcpy)|在读取和写入文件时重写以修改内存复制行为。|
|[CMemFile：：真实](#realloc)|重写以修改内存重新分配行为。|

## <a name="remarks"></a>备注

这些内存文件与磁盘文件类似，只不过文件存储在 RAM 中而不是磁盘上。 内存文件可用于快速临时存储或在独立进程之间传输原始字节或序列化对象。

`CMemFile`对象可以自动分配自己的内存，`CMemFile`也可以通过调用[Attach](#attach)将您自己的内存块附加到对象。 在这两种情况下，如果`nGrowBytes``nGrowBytes`不是零，则自动以 -大小增量分配用于自动增长内存文件的内存。

如果内存最初由`CMemFile``CMemFile`对象分配，则在破坏对象时将自动删除内存块;否则，您负责释放附加到对象的内存。

您可以通过调用`CMemFile`[Detach](#detach)将其从对象分离时提供的指针访问内存块。

最常见的用途`CMemFile`是创建对象`CMemFile`，并通过调用[CFile](../../mfc/reference/cfile-class.md)成员函数使用它。 请注意，创建一`CMemFile`个自动打开它：您不调用[CFile：：open](../../mfc/reference/cfile-class.md#open)，仅用于磁盘文件。 由于`CMemFile`不使用磁盘文件，因此不使用数据成员`CFile::m_hFile`。

`CFile`成员函数["重复](../../mfc/reference/cfile-class.md#duplicate)"、[锁定范围](../../mfc/reference/cfile-class.md#lockrange)和[解锁范围](../../mfc/reference/cfile-class.md#unlockrange)未为`CMemFile`实现。 如果在`CMemFile`对象上调用这些函数，您将获得[CNot 支持异常](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile`使用运行时库函数[malloc、realloc](../../c-runtime-library/reference/malloc.md)[和自由分配](../../c-runtime-library/reference/free.md)、重新分配和分配内存; [realloc](../../c-runtime-library/reference/realloc.md)和内在[的memcpy，](../../c-runtime-library/reference/memcpy-wmemcpy.md)以阻止复制记忆，当阅读和写作。 如果要在增长文件时`CMemFile`更改此行为或行为，请从`CMemFile`相应的函数派生您自己的类并重写相应的函数。

有关 的详细信息`CMemFile`，请参阅[MFC](../../mfc/files-in-mfc.md)和[内存管理 （MFC）](../../mfc/memory-management.md)中的文章文件，并在*运行时库参考*中查看[文件处理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile：Alloc

此函数由`CMemFile`成员函数调用。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要分配的内存字节数。

### <a name="return-value"></a>返回值

指向已分配的内存块的指针;如果分配失败，则为 NULL。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存分配。 如果重写此函数，您可能还希望覆盖[Free](#free)和[Realloc。](#realloc)

默认实现使用运行时库函数[malloc](../../c-runtime-library/reference/malloc.md)分配内存。

## <a name="cmemfileattach"></a><a name="attach"></a>CMem文件：附加

调用此函数以将内存块附加到`CMemFile`。

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*lpBuffer*<br/>
指向要附加到 的缓冲区`CMemFile`的指针。

*n缓冲区大小*<br/>
以字节为单位指定缓冲区大小的整数。

*n 增长字节*<br/>
内存分配以字节为单位递增。

### <a name="remarks"></a>备注

这将导致`CMemFile`使用内存块作为内存文件。

如果*nGrowBytes*为`CMemFile`0，则将文件长度设置为*nBufferSize*。 这意味着内存块中的数据在附加到之前`CMemFile`将用作文件。 无法以这种方式创建的内存文件。

由于无法扩展文件，请注意不要导致`CMemFile`尝试扩展文件。 例如，不要调用 CFile`CMemFile`的重写[：写入](../../mfc/reference/cfile-class.md#write)结尾写入，或者不调用[CFile：设置](../../mfc/reference/cfile-class.md#setlength)长度超过*nBufferSize*的长度长度。

如果*nGrowBytes*大于 0，`CMemFile`将忽略已连接的内存块的内容。 您必须使用`CMemFile`重写 从头开始编写内存文件的内容`CFile::Write`。 如果尝试写入文件末尾或通过调用`CMemFile`的`CFile::SetLength`重写来增长文件，`CMemFile`则以*nGrowBytes*的增量增加内存分配。 如果传递给的内存块`Attach`未使用与[Alloc](#alloc)兼容的方法分配，则增长内存分配将失败。 要与 的默认实现兼容`Alloc`，必须使用运行时库函数 malloc 或[calloc](../../c-runtime-library/reference/malloc.md)分配内存[calloc](../../c-runtime-library/reference/calloc.md)。

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMem文件：CMemFile

第一个重载将打开一个空内存文件。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>参数

*n 增长字节*<br/>
内存分配以字节为单位递增。

*lpBuffe*r 指针指向一个缓冲区，该缓冲区接收大小*nBufferSize*的信息。

*n缓冲区大小*<br/>
指定文件缓冲区大小的整数（以字节为单位）。

### <a name="remarks"></a>备注

请注意，该文件由构造函数打开，并且不应调用[CFile：：：：打开](../../mfc/reference/cfile-class.md#open)。

第二个重载的作用与使用第一个构造函数并立即调用具有相同参数的[Attach](#attach)相同。 有关详细信息，请参阅`Attach`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile：:D

调用此函数以获取指向 正在使用的内存块的`CMemFile`指针。

```
BYTE* Detach();
```

### <a name="return-value"></a>返回值

指向包含内存文件内容的内存块的指针。

### <a name="remarks"></a>备注

调用此函数也会关闭`CMemFile`。 您可以通过调用[Attach](#attach)将内存块`CMemFile`重新附加到 。 如果要重新连接文件并使用其中的数据，则应调用[CFile：：getLength](../../mfc/reference/cfile-class.md#getlength)以在调用`Detach`之前获取文件的长度。 请注意，如果将内存块附加到 ，`CMemFile`以便可以使用其数据 （= `nGrowBytes` 0），则将无法扩展内存文件。

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile：免费

此函数由`CMemFile`成员函数调用。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指针指向要处理的内存。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存处理。 如果重写此函数，您可能还希望重写[Alloc](#alloc)和[Realloc。](#realloc)

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile：：增长文件

此函数由多个`CMemFile`成员函数调用。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>参数

*德纽伦*<br/>
内存文件的新大小。

### <a name="remarks"></a>备注

如果要更改其文件的增长方式`CMemFile`，可以重写它。 默认实现调用[Realloc](#realloc)来扩展现有块（或[Alloc](#alloc)以创建内存块），以构造函数或[Attach](#attach) `nGrowBytes`调用中指定的值的倍数分配内存。

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile：Memcpy

此函数由`CMemFile` [CFile：：读取](../../mfc/reference/cfile-class.md#read)和[CFile：：写入](../../mfc/reference/cfile-class.md#write)以传输数据到内存文件并从内存文件。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMemTarget*<br/>
指向要将源内存复制到的内存块的指针。

*lpMem 来源*<br/>
指向源内存块的指针。

*n 字节*<br/>
要复制的字节数。

### <a name="return-value"></a>返回值

*lpMemTarget*的副本。

### <a name="remarks"></a>备注

如果要更改执行这些内存副本的方式，`CMemFile`则重写此函数。

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile：：真实

此函数由`CMemFile`成员函数调用。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>参数

*lpMem*<br/>
指向要重新分配的内存块的指针。

*n 字节*<br/>
内存块的新大小。

### <a name="return-value"></a>返回值

如果重新分配失败，则指向重新分配（并可能移动）的内存块的指针。

### <a name="remarks"></a>备注

重写此函数以实现自定义内存重新分配。 如果重写此函数，您可能还希望重写[Alloc](#alloc)和[Free。](#free)

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
