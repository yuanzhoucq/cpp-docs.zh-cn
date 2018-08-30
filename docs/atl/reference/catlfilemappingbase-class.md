---
title: CAtlFileMappingBase 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f07f14cca7ea0346cc6772d3dca959af07a05cd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218157"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 类
此类表示一个内存映射文件。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|构造函数。|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|调用此方法以将文件映射对象的复制。|  
|[CAtlFileMappingBase::GetData](#getdata)|调用此方法以获取文件映射对象中的数据。|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|调用此方法返回的文件句柄。|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|调用此方法以获取映射大小从文件映射对象。|  
|[CAtlFileMappingBase::MapFile](#mapfile)|调用此方法以创建文件映射对象。|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|调用此方法以创建允许完全访问权限的所有进程的文件映射对象。|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|调用此方法以返回到的文件映射对象的句柄。|  
|[CAtlFileMappingBase::Unmap](#unmap)|调用此方法来取消映射文件映射对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|将当前的文件映射对象设置为另一个文件映射对象。|  
  
## <a name="remarks"></a>备注  
 文件映射是与进程的虚拟地址空间的一部分的文件的内容关联。 此类提供用于创建使程序轻松地访问和共享数据的文件映射对象的方法。  
  
 有关详细信息，请参阅[文件映射](/windows/desktop/Memory/file-mapping)Windows SDK 中。  
  
## <a name="requirements"></a>要求  
 **标头：** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase  
 构造函数。  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>参数  
 *orig*  
 要复制以创建新对象的原始文件映射对象。  
  
### <a name="remarks"></a>备注  
 创建一个新的文件映射对象，可选择使用现有对象。 若要调用仍有必要[CAtlFileMappingBase::MapFile](#mapfile)若要打开或创建特定文件的文件映射对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>  CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 析构函数。  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放任何资源分配的类并调用[CAtlFileMappingBase::Unmap](#unmap)方法。  
  
##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom  
 调用此方法以将文件映射对象的复制。  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>参数  
 *orig*  
 要从复制的原始文件映射对象。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
##  <a name="getdata"></a>  CAtlFileMappingBase::GetData  
 调用此方法以获取文件映射对象中的数据。  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向数据。  
  
##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle  
 调用此方法以返回到的文件映射对象的句柄。  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>返回值  
 返回的句柄的文件映射对象。  
  
##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize  
 调用此方法以获取映射大小从文件映射对象。  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回映射的大小。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile  
 调用此方法来打开或创建指定的文件的文件映射对象。  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>参数  
 *hFile*  
 从其创建映射对象的文件的句柄。 *hFile*必须是有效并且不能设置为 INVALID_HANDLE_VALUE。  
  
 *nMappingSize*  
 映射的大小。 如果为 0，则文件映射对象的最大大小等同于由标识的文件的当前大小*hFile。*  
  
 *nOffset*  
 映射的开始位置的文件偏移量。 偏移量的值必须是系统的内存分配粒度的倍数。  
  
 *dwMappingProtection*  
 所需的文件视图的映射文件时保护。 请参阅*flProtect*中[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK 中。  
  
 *dwViewDesiredAccess*  
 指定在文件视图和映射文件的页保护，因此，对的访问类型。 请参阅*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 创建文件映射对象后，文件的大小不能超过文件映射对象中; 的大小如果是这样，并非所有文件的内容可供共享。 有关更多详细信息，请参阅[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)并[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem  
 调用此方法以创建允许完全访问权限的所有进程的文件映射对象。  
  
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
 *nMappingSize*  
 映射的大小。 如果为 0，最大大小的文件映射对象是否等于标识的文件映射对象的当前大小*szName*。  
  
 *szName*  
 映射对象的名称。  
  
 *pbAlreadyExisted*  
 指向一个 BOOL 值，设置为 TRUE 的映射对象已存在。  
  
 *lpsa*  
 将指针与`SECURITY_ATTRIBUTES`结构，它确定返回的句柄能否由子进程继承。 请参阅*lpAttributes*中[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK 中。  
  
 *dwMappingProtection*  
 在文件视图中，映射文件时所需的保护。 请参阅*flProtect*中`CreateFileMapping`Windows SDK 中。  
  
 *dwViewDesiredAccess*  
 指定在文件视图和映射文件的页保护，因此，对的访问类型。 请参阅*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `MapShareMem` 允许创建的现有文件映射对象[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)，以在不同进程之间共享。  
  
##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping  
 调用此方法以打开指定文件的命名的文件映射对象。  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>参数  
 *szName*  
 映射对象的名称。 如果没有此名称的文件映射对象的打开句柄，并且所映射对象上的安全描述符不与冲突*dwViewDesiredAccess*参数打开操作成功。  
  
 *nMappingSize*  
 映射的大小。 如果为 0，最大大小的文件映射对象是否等于标识的文件映射对象的当前大小*szName*。  
  
 *nOffset*  
 映射的开始位置的文件偏移量。 偏移量的值必须是系统的内存分配粒度的倍数。  
  
 *dwViewDesiredAccess*  
 指定在文件视图和映射文件的页保护，因此，对的访问类型。 请参阅*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果输入的参数无效，将会出错断言。  
  
##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =  
 将当前的文件映射对象设置为另一个文件映射对象。  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>参数  
 *orig*  
 当前的文件映射对象。  
  
### <a name="return-value"></a>返回值  
 返回对当前对象的引用。  
  
##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap  
 调用此方法来取消映射文件映射对象。  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 请参阅[UnmapViewOfFile](https://msdn.microsoft.com/library/windows/desktop/aa366882)适用于更多详细信息的 Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [CAtlFileMapping 类](../../atl/reference/catlfilemapping-class.md)   
 [类概述](../../atl/atl-class-overview.md)
