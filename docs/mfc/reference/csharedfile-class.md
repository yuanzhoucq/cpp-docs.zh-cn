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
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502604"
---
# <a name="csharedfile-class"></a>CSharedFile 类

支持共享内存文件的[CMemFile](../../mfc/reference/cmemfile-class.md)派生类。

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
|[CSharedFile::Detach](#detach)|关闭共享内存文件并返回其内存块的句柄。|
|[CSharedFile::SetHandle](#sethandle)|将共享内存文件附加到内存块。|

## <a name="remarks"></a>备注

内存文件的行为类似于磁盘文件。 差别在于, 内存文件存储在 RAM 中, 而不是存储在磁盘上。 内存文件可用于快速临时存储, 或者用于在独立进程之间传输原始字节或序列化的对象。

共享内存文件与其他内存文件的不同之处在于, 内存文件是用[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函数分配的。 类将数据存储在全局分配的内存块 (使用`GlobalAlloc`创建) 中, 可以使用 DDE、剪贴板或其他 OLE/COM 统一数据传输操作 (例如, 使用`IDataObject`) 共享此内存块。 `CSharedFile`

`GlobalAlloc`返回一个 HGLOBAL 句柄, 而不是指向内存的指针, 如[malloc](../../c-runtime-library/reference/malloc.md)返回的指针。 某些应用程序需要 HGLOBAL 句柄。 例如, 若要将数据放在剪贴板上, 则需要一个 HGLOBAL 句柄。

`CSharedFile`不使用内存映射文件, 并且不能在进程之间直接共享数据。

`CSharedFile`对象可以自动分配其自己的内存。 或者, 可以通过调用[CSharedFile:: SetHandle](#sethandle)将自己`CSharedFile`的内存块附加到对象。 在这两种情况下, 如果`nGrowBytes` `nGrowBytes`不是零, 则会按大小增加自动分配内存文件的内存。

有关详细信息, 请参阅《*运行时库参考*中的文章[文件在 MFC](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>要求

**标头:** afxadv

##  <a name="csharedfile"></a>CSharedFile::CSharedFile

构造一个`CSharedFile`对象并为其分配内存。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>参数

*nAllocFlags*<br/>
指示如何分配内存的标志。 有关有效标志值的列表, 请参阅[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) 。

*nGrowBytes*<br/>
内存分配递增量 (以字节为单位)。

##  <a name="detach"></a>CSharedFile::D etach

调用此函数可关闭内存文件并将其与内存块分离。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>返回值

包含内存文件内容的内存块的句柄。

### <a name="remarks"></a>备注

可以通过使用**分离**返回的句柄, 通过调用[SetHandle](#sethandle)来重新打开它。

##  <a name="sethandle"></a>CSharedFile::SetHandle

调用此函数可将全局内存块附加到`CSharedFile`对象。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>参数

*hGlobalMemory*<br/>
要附加到的`CSharedFile`全局内存的句柄。

*bAllowGrow*<br/>
指定是否允许内存块增长。

### <a name="remarks"></a>备注

如果*bAllowGrow*的值为非零值, 则会根据需要增加内存块的大小, 例如, 如果尝试将更多字节写入到文件, 而不是内存块的大小。

## <a name="see-also"></a>请参阅

[CMemFile 类](../../mfc/reference/cmemfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
