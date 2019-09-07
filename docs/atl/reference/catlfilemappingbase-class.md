---
title: CAtlFileMappingBase 类
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: a20a8f6c00f9404aa819b87a6a69ad2c08fb4561
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739552"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 类

此类表示内存映射文件。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CAtlFileMappingBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|构造函数。|
|[CAtlFileMappingBase：： ~ CAtlFileMappingBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|调用此方法可从文件映射对象复制。|
|[CAtlFileMappingBase::GetData](#getdata)|调用此方法可从文件映射对象获取数据。|
|[CAtlFileMappingBase::GetHandle](#gethandle)|调用此方法以返回文件句柄。|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|调用此方法可从文件映射对象获取映射大小。|
|[CAtlFileMappingBase::MapFile](#mapfile)|调用此方法可创建文件映射对象。|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|调用此方法可创建一个允许对所有进程具有完全访问权限的文件映射对象。|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|调用此方法以返回文件映射对象的句柄。|
|[CAtlFileMappingBase::Unmap](#unmap)|调用此方法可取消映射文件映射对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAtlFileMappingBase：： operator =](#operator_eq)|将当前文件映射对象设置为另一个文件映射对象。|

## <a name="remarks"></a>备注

文件映射是文件内容与进程的部分虚拟地址空间的关联。 此类提供用于创建文件映射对象的方法，这些对象允许程序轻松访问和共享数据。

有关详细信息，请参阅 Windows SDK 中的[文件映射](/windows/win32/Memory/file-mapping)。

## <a name="requirements"></a>要求

**标头：** atlfile

##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

构造函数。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>参数

*orig*<br/>
要复制以创建新对象的原始文件映射对象。

### <a name="remarks"></a>备注

使用现有对象创建一个新的文件映射对象（可选）。 仍需要调用[CAtlFileMappingBase：：](#mapfile) mapping 来打开或创建特定文件的文件映射对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>CAtlFileMappingBase：： ~ CAtlFileMappingBase

析构函数。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>备注

释放由类分配的任何资源，并调用[CAtlFileMappingBase：：取消映射](#unmap)方法。

##  <a name="copyfrom"></a>CAtlFileMappingBase：： CopyFrom

调用此方法可从文件映射对象复制。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>参数

*orig*<br/>
要从中进行复制的原始文件映射对象。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

##  <a name="getdata"></a>CAtlFileMappingBase：：

调用此方法可从文件映射对象获取数据。

```
void* GetData() const throw();
```

### <a name="return-value"></a>返回值

返回指向数据的指针。

##  <a name="gethandle"></a>CAtlFileMappingBase：： GetHandle

调用此方法以返回文件映射对象的句柄。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>返回值

返回文件映射对象的句柄。

##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

调用此方法可从文件映射对象获取映射大小。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>返回值

返回映射大小。

### <a name="example"></a>示例

请参阅[CAtlFileMappingBase：： CAtlFileMappingBase](#catlfilemappingbase)的示例。

##  <a name="mapfile"></a>CAtlFileMappingBase：：映射

调用此方法可打开或创建指定文件的文件映射对象。

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>参数

*hFile*<br/>
要从中创建映射对象的文件的句柄。 *hFile*必须是有效的，并且不能设置为 INVALID_HANDLE_VALUE。

*nMappingSize*<br/>
映射大小。 如果为0，则文件映射对象的最大大小等于由 HFile 标识的文件的当前大小 *。*

*nOffset*<br/>
要开始映射的文件偏移量。 偏移量值必须是系统内存分配粒度的倍数。

*dwMappingProtection*<br/>
文件在映射时所需的保护。 请参阅 Windows SDK 的[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*flProtect* 。

*dwViewDesiredAccess*<br/>
指定对文件视图的访问类型，因此还指定对由文件映射的页面的保护。 请参阅 Windows SDK 的[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中的*dwDesiredAccess* 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

创建文件映射对象之后，该文件的大小不得超过文件映射对象的大小;如果是这样，则并非文件的所有内容都可用于共享。 有关更多详细信息，请参阅 Windows SDK 中的[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)和[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 。

### <a name="example"></a>示例

请参阅[CAtlFileMappingBase：： CAtlFileMappingBase](#catlfilemappingbase)的示例。

##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

调用此方法可创建一个允许对所有进程具有完全访问权限的文件映射对象。

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>参数

*nMappingSize*<br/>
映射大小。 如果为0，则文件映射对象的最大大小等于*szName*标识的文件映射对象的当前大小。

*szName*<br/>
映射对象的名称。

*pbAlreadyExisted*<br/>
指向一个布尔值，如果映射对象已存在，则该布尔值设置为 TRUE。

*lpsa*<br/>
指向`SECURITY_ATTRIBUTES`结构的指针，该结构确定返回的句柄是否可以由子进程继承。 请参阅 Windows SDK 的[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*lpAttributes* 。

*dwMappingProtection*<br/>
文件视图所需的保护（在映射文件时）。 请参阅 Windows SDK `CreateFileMapping`中的 flProtect。

*dwViewDesiredAccess*<br/>
指定对文件视图的访问类型，因此还指定对由文件映射的页面的保护。 请参阅 Windows SDK 的[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中的*dwDesiredAccess* 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

`MapShareMem`允许通过[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)创建的现有文件映射对象在进程之间共享。

##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

调用此方法以打开指定文件的已命名文件映射对象。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>参数

*szName*<br/>
映射对象的名称。 如果具有此名称的文件映射对象的打开句柄，并且映射对象上的安全描述符不与*dwViewDesiredAccess*参数冲突，则打开操作将成功。

*nMappingSize*<br/>
映射大小。 如果为0，则文件映射对象的最大大小等于*szName*标识的文件映射对象的当前大小。

*nOffset*<br/>
要开始映射的文件偏移量。 偏移量值必须是系统内存分配粒度的倍数。

*dwViewDesiredAccess*<br/>
指定对文件视图的访问类型，因此还指定对由文件映射的页面的保护。 请参阅 Windows SDK 的[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中的*dwDesiredAccess* 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

在调试版本中，如果输入参数无效，则将发生断言错误。

##  <a name="operator_eq"></a>CAtlFileMappingBase：： operator =

将当前文件映射对象设置为另一个文件映射对象。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>参数

*orig*<br/>
当前文件映射对象。

### <a name="return-value"></a>返回值

返回对当前对象的引用。

##  <a name="unmap"></a>CAtlFileMappingBase：：取消映射

调用此方法可取消映射文件映射对象。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

有关更多详细信息，请参阅 Windows SDK 中的[UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) 。

## <a name="see-also"></a>请参阅

[CAtlFileMapping 类](../../atl/reference/catlfilemapping-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
