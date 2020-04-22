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
ms.openlocfilehash: 16eebfff4330a47888d1b60eaa993ee87d120f72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748292"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 类

此类表示内存映射的文件。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CAtlFileMappingBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtl文件映射库：：CAtlFile映射库](#catlfilemappingbase)|构造函数。|
|[CAtl文件映射库：：_CAtlFile映射库](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlFile映射基础：：从](#copyfrom)|调用此方法从文件映射对象复制。|
|[CAtlFile映射基础：获取数据](#getdata)|调用此方法从文件映射对象获取数据。|
|[CAtlFile映射基础：：获取手柄](#gethandle)|调用此方法以返回文件句柄。|
|[CAtlFile映射基础：：获取映射大小](#getmappingsize)|调用此方法从文件映射对象获取映射大小。|
|[CAtlFile映射基础：：地图文件](#mapfile)|调用此方法以创建文件映射对象。|
|[CAtlFile映射基础：：映射共享Mem](#mapsharedmem)|调用此方法以创建允许完全访问所有进程的文件映射对象。|
|[CAtlFile映射基础：：打开映射](#openmapping)|调用此方法以将句柄返回到文件映射对象。|
|[CAtlFile映射基础：：取消映射](#unmap)|调用此方法以取消映射文件映射对象。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlFile映射基础：：运算符 |](#operator_eq)|将当前文件映射对象设置到另一个文件映射对象。|

## <a name="remarks"></a>备注

文件映射是文件内容与进程虚拟地址空间的一部分的关联。 此类提供了创建文件映射对象的方法，允许程序轻松访问和共享数据。

有关详细信息，请参阅 Windows SDK 中[的文件映射](/windows/win32/Memory/file-mapping)。

## <a name="requirements"></a>要求

**标题：** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtl文件映射库：：CAtlFile映射库

构造函数。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>参数

*奥里格*<br/>
要复制的原始文件映射对象以创建新对象。

### <a name="remarks"></a>备注

创建新的文件映射对象，可以选择使用现有对象。 仍需要调用[CAtlFileMappingBase：mapFile](#mapfile)来打开或创建特定文件的文件映射对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtl文件映射库：：_CAtlFile映射库

析构函数。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>备注

释放类分配的任何资源，并调用[CAtlFileMappingBase：：unmap](#unmap)方法。

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFile映射基础：：从

调用此方法从文件映射对象复制。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>参数

*奥里格*<br/>
要复制的原始文件映射对象。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFile映射基础：获取数据

调用此方法从文件映射对象获取数据。

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>返回值

返回指向数据的指针。

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFile映射基础：：获取手柄

调用此方法以将句柄返回到文件映射对象。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>返回值

返回文件映射对象的句柄。

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFile映射基础：：获取映射大小

调用此方法从文件映射对象获取映射大小。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>返回值

返回映射大小。

### <a name="example"></a>示例

请参阅[CAtlFile 映射库的示例：CAtlFile映射库](#catlfilemappingbase)。

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFile映射基础：：地图文件

调用此方法以打开或创建指定文件的文件映射对象。

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
处理从中创建映射对象的文件。 *hFile*必须有效且不能设置为INVALID_HANDLE_VALUE。

*n映射大小*<br/>
映射大小。 如果为 0，则文件映射对象的最大大小等于*hFile*标识的文件的当前大小。

*n偏移*<br/>
要开始映射的文件偏移量。 偏移值必须是系统内存分配粒度的倍数。

*dwMapping保护*<br/>
映射文件时文件视图所需的保护。 请参阅在 Windows SDK 中[创建文件映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*fl 保护*。

*dwView 希望访问*<br/>
指定访问文件视图的类型，因此，指定文件映射的页面的保护。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

创建文件映射对象后，文件的大小不得超过文件映射对象的大小;如果是，则并非所有文件的内容都可供共享。 有关详细信息，请参阅在 Windows SDK 中[创建文件映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)和[MapViewFileEx。](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)

### <a name="example"></a>示例

请参阅[CAtlFile 映射库的示例：CAtlFile映射库](#catlfilemappingbase)。

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFile映射基础：：映射共享Mem

调用此方法以创建允许完全访问所有进程的文件映射对象。

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

*n映射大小*<br/>
映射大小。 如果为 0，则文件映射对象的最大大小等于*szName*标识的文件映射对象的当前大小。

*sz名称*<br/>
映射对象的名称。

*pb 已存在*<br/>
指向如果映射对象已存在，则设置为 TRUE 的 BOOL 值。

*lpsa*<br/>
指向结构的`SECURITY_ATTRIBUTES`指针，用于确定返回的句柄是否可以由子进程继承。 请参阅在 Windows SDK 中[创建文件映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*lp 属性*。

*dwMapping保护*<br/>
映射文件时文件视图所需的保护。 请参阅*flProtect*Windows `CreateFileMapping` SDK 中的 fl 保护。

*dwView 希望访问*<br/>
指定访问文件视图的类型，因此，指定文件映射的页面的保护。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

`MapShareMem`允许在进程之间共享由[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)创建的现有文件映射对象。

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFile映射基础：：打开映射

调用此方法以打开指定文件的命名文件映射对象。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>参数

*sz名称*<br/>
映射对象的名称。 如果此名称对文件映射对象有打开的句柄，并且映射对象上的安全描述符不与*dwView希望访问*参数冲突，则打开操作将成功。

*n映射大小*<br/>
映射大小。 如果为 0，则文件映射对象的最大大小等于*szName*标识的文件映射对象的当前大小。

*n偏移*<br/>
要开始映射的文件偏移量。 偏移值必须是系统内存分配粒度的倍数。

*dwView 希望访问*<br/>
指定访问文件视图的类型，因此，指定文件映射的页面的保护。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

在调试生成中，如果输入参数无效，将发生断言错误。

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFile映射基础：：运算符 |

将当前文件映射对象设置到另一个文件映射对象。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>参数

*奥里格*<br/>
当前文件映射对象。

### <a name="return-value"></a>返回值

返回对当前对象的引用。

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFile映射基础：：取消映射

调用此方法以取消映射文件映射对象。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的["取消映射查看文件](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile)"。

## <a name="see-also"></a>请参阅

[CAtlFileMapping 类](../../atl/reference/catlfilemapping-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
