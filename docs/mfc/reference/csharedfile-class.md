---
title: C 共享文件类
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: c715ca1b8a2b647f89ada008f3c6606ca5e58783
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750392"
---
# <a name="csharedfile-class"></a>C 共享文件类

支持共享内存文件的[CMemFile](../../mfc/reference/cmemfile-class.md)派生类。

## <a name="syntax"></a>语法

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 共享文件：C 共享文件](#csharedfile)|构造 `CSharedFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[共享文件：:D](#detach)|关闭共享内存文件并返回其内存块的句柄。|
|[C 共享文件：：设置句柄](#sethandle)|将共享内存文件附加到内存块。|

## <a name="remarks"></a>备注

内存文件与磁盘文件一样。 区别在于，内存文件存储在 RAM 中，而不是存储在磁盘上。 内存文件可用于快速临时存储，或用于在独立进程之间传输原始字节或序列化对象。

共享内存文件与其他内存文件不同，因为内存是使用[Global Alloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函数分配的。 类`CSharedFile`将数据存储在全局分配的内存块中（使用`GlobalAlloc`创建），并且此内存块可以使用 DDE、剪贴板或其他 OLE/COM 统一数据传输操作（例如，使用`IDataObject`）共享。

`GlobalAlloc`返回 HGLOBAL 句柄，而不是指向内存的指针，例如[malloc](../../c-runtime-library/reference/malloc.md)返回的指针。 某些应用程序需要 HGLOBAL 句柄。 例如，要将数据放在剪贴板上，您需要一个 HGLOBAL 句柄。

`CSharedFile`不使用内存映射的文件，并且数据不能直接在进程之间共享。

`CSharedFile`对象可以自动分配自己的内存。 或者，您可以通过调用`CSharedFile`[CSharedFile：：setHandle](#sethandle)将您自己的内存块附加到对象。 在这两种情况下，自动增长内存文件的内存分配以`nGrowBytes`-大小增量（如果不是零）。 `nGrowBytes`

有关详细信息，请参阅运行时*库参考*[中的 MFC](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)中的文章文件。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>要求

**标题：** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>C 共享文件：C 共享文件

构造对象`CSharedFile`并为其分配内存。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>参数

*nAllocFlags*<br/>
指示如何分配内存的标志。 有关有效标志值的列表，请参阅[GlobalAlloc。](/windows/win32/api/winbase/nf-winbase-globalalloc)

*n 增长字节*<br/>
内存分配以字节为单位递增。

## <a name="csharedfiledetach"></a><a name="detach"></a>共享文件：:D

调用此函数以关闭内存文件并将其从内存块中分离。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>返回值

包含内存文件内容的内存块的句柄。

### <a name="remarks"></a>备注

您可以使用**Detach**返回的句柄调用[SetHandle](#sethandle)来重新打开它。

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>C 共享文件：：设置句柄

调用此函数以将全局内存块附加到`CSharedFile`对象。

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>参数

*h全球内存*<br/>
处理要附加到 的全局内存。 `CSharedFile`

*bAllow增长*<br/>
指定是否允许内存块增长。

### <a name="remarks"></a>备注

如果*bAllowGrow*是非零，则内存块的大小会根据需要增加，例如，如果您尝试向文件写入比内存块大小更多的字节。

## <a name="see-also"></a>请参阅

[CMemFile 类](../../mfc/reference/cmemfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
