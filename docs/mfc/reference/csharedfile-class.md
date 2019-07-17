---
title: CSharedFile 类
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
ms.openlocfilehash: 0a9bbf3072a665c04501025d421839fa90a37225
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344423"
---
# <a name="csharedfile-class"></a>CSharedFile 类

[CMemFile](../../mfc/reference/cmemfile-class.md)-支持的派生的类共享内存文件。

## <a name="syntax"></a>语法

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|构造 `CSharedFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|关闭共享的内存文件并返回其内存块的句柄。|
|[CSharedFile::SetHandle](#sethandle)|将共享的内存文件附加到的内存块。|

## <a name="remarks"></a>备注

内存文件类似于磁盘文件。 其差异是，在 RAM 中，而不是磁盘上存储的内存文件。 对于快速临时存储空间，或者传输原始字节或序列化的对象之间独立进程内存文件。

共享的内存文件不同于其他内存文件，因为它们的内存分配带有[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函数。 `CSharedFile`类将数据存储在全局范围内分配的内存块 (使用创建`GlobalAlloc`)，并且该内存块可以共享使用 DDE、 剪贴板或其他 OLE/COM 统一数据传输操作，例如，使用`IDataObject`。

`GlobalAlloc` 返回 HGLOBAL 处理而不是指向内存，如所返回的指针的指针[malloc](../../c-runtime-library/reference/malloc.md)。 在某些应用程序需要 HGLOBAL 句柄。 例如，若要将数据放到剪贴板上需要 HGLOBAL 句柄。

`CSharedFile` 不使用内存映射文件和数据不能直接进程之间共享。

`CSharedFile` 对象可以自动分配其自己的内存。 或者，可以将附加到你自己的内存块`CSharedFile`对象通过调用[CSharedFile::SetHandle](#sethandle)。 在任一情况下，自动增大内存文件的内存分配中`nGrowBytes`-如果大小为增量`nGrowBytes`不为零。

有关详细信息，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)并[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>要求

**标头：** afxadv.h

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

构造`CSharedFile`对象，并为它分配内存。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>参数

*nAllocFlags*<br/>
标志，指示内存的分配方式。 请参阅[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)有关有效的标志值的列表。

*nGrowBytes*<br/>
内存分配的增量以字节为单位。

##  <a name="detach"></a>  CSharedFile::Detach

调用此函数可关闭内存文件并从内存块对其进行分离。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>返回值

包含内存文件的内容的内存块的句柄。

### <a name="remarks"></a>备注

你可以通过调用重新打开它[SetHandle](#sethandle)，使用返回的句柄**分离**。

##  <a name="sethandle"></a>  CSharedFile::SetHandle

调用此函数可将附加到全局内存块`CSharedFile`对象。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>参数

*hGlobalMemory*<br/>
要附加到的全局内存句柄`CSharedFile`。

*bAllowGrow*<br/>
指定是否可以增长的内存块。

### <a name="remarks"></a>备注

如果*bAllowGrow*为非零值，增加了大小的内存块的必要时，例如，如果你尝试将更多的字节写入内存块的大小比文件。

## <a name="see-also"></a>请参阅

[CMemFile 类](../../mfc/reference/cmemfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
