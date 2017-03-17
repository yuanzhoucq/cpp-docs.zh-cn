---
title: "CAtlFileMappingBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 439f123bc0addbbec2a26102d0197d0a1f14a8d5
ms.lasthandoff: 02/24/2017

---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 类
此类表示一个内存映射文件。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|构造函数。|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|调用此方法以将复制的文件映射对象。|  
|[CAtlFileMappingBase::GetData](#getdata)|调用此方法以从文件映射对象获取数据。|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|调用此方法返回的文件句柄。|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|调用此方法以获取从文件映射对象的映射的大小。|  
|[CAtlFileMappingBase::MapFile](#mapfile)|调用此方法以创建文件映射对象。|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|调用此方法以创建一个文件映射对象，它允许完全访问权限的所有进程。|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|调用此方法以返回到文件映射对象的句柄。|  
|[CAtlFileMappingBase::Unmap](#unmap)|调用此方法来取消映射文件映射对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|将当前的文件映射对象设置为另一个文件映射对象。|  
  
## <a name="remarks"></a>备注  
 文件映射是与进程的虚拟地址空间的部分相关联的文件的内容。 此类提供用于创建允许程序轻松地访问和共享数据的文件映射对象的方法。  
  
 有关详细信息，请参阅[文件映射](http://msdn.microsoft.com/library/windows/desktop/aa366556)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase  
 构造函数。  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>参数  
 `orig`  
 要复制以创建新对象的原始文件映射对象。  
  
### <a name="remarks"></a>备注  
 创建一个新的文件映射对象，可以选择使用现有对象。 仍然必须调用[CAtlFileMappingBase::MapFile](#mapfile)打开或创建特定文件的文件映射对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&71;](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 析构函数。  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>备注  
 释放由类和调用分配的任何资源[CAtlFileMappingBase::Unmap](#unmap)方法。  
  
##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom  
 调用此方法以将复制的文件映射对象。  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>参数  
 `orig`  
 要从复制的原始文件映射对象。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
##  <a name="getdata"></a>CAtlFileMappingBase::GetData  
 调用此方法以从文件映射对象获取数据。  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回对数据的指针。  
  
##  <a name="gethandle"></a>CAtlFileMappingBase::GetHandle  
 调用此方法以返回到文件映射对象的句柄。  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>返回值  
 返回文件映射对象的句柄。  
  
##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize  
 调用此方法以获取从文件映射对象的映射的大小。  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回映射的大小。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapfile"></a>CAtlFileMappingBase::MapFile  
 调用此方法来打开或创建指定文件的文件映射对象。  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>参数  
 `hFile`  
 要创建映射对象从其文件的句柄。 `hFile`必须是有效并且不能设置为 INVALID_HANDLE_VALUE。  
  
 `nMappingSize`  
 映射大小中。 如果为 0，则文件映射对象的最大大小等同于由标识的文件的当前大小*hFile。*  
  
 `nOffset`  
 文件偏移量映射即将开始。 偏移量的值必须是系统的内存分配粒度的倍数。  
  
 `dwMappingProtection`  
 在映射文件时所需的文件视图的保护。 请参阅`flProtect`中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwViewDesiredAccess`  
 指定的文件视图和映射文件的页保护，因此，对访问的类型。 请参阅`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 创建文件映射对象后，该文件的大小不得超过文件映射对象中; 的大小如果是这样，并非所有文件的内容将可供共享。 有关详细信息，请参阅[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)和[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem  
 调用此方法以创建一个文件映射对象，它允许完全访问权限的所有进程。  
  
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
 `nMappingSize`  
 映射大小中。 如果为 0，则文件映射对象的最大大小等同于由标识的文件映射对象的当前大小`szName.`  
  
 `szName`  
 映射对象的名称。  
  
 *pbAlreadyExisted*  
 指向一个 BOOL 值，则设置为 TRUE 的映射对象已存在。  
  
 `lpsa`  
 将指针与**SECURITY_ATTRIBUTES**结构，它确定是否可以由子进程继承返回的句柄。 请参阅*lpAttributes*中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwMappingProtection`  
 文件视图中，在映射文件时所需的保护。 请参阅`flProtect`中**CreateFileMapping**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwViewDesiredAccess`  
 指定的文件视图和映射文件的页保护，因此，对访问的类型。 请参阅`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 **MapShareMem**允许通过创建的现有文件映射对象[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)、 两个进程之间共享。  
  
##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping  
 调用此方法以打开指定文件的命名的文件映射对象。  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>参数  
 `szName`  
 映射对象的名称。 如果按此名称的文件映射对象的打开句柄，并且不与冲突映射对象上的安全描述符`dwViewDesiredAccess`参数，打开操作成功。  
  
 `nMappingSize`  
 映射大小中。 如果为 0，则文件映射对象的最大大小等同于由标识的文件映射对象的当前大小`szName.`  
  
 `nOffset`  
 文件偏移量映射即将开始。 偏移量的值必须是系统的内存分配粒度的倍数。  
  
 `dwViewDesiredAccess`  
 指定的文件视图和映射文件的页保护，因此，对访问的类型。 请参阅`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 在调试版本中，则断言会错误如果输入的参数无效。  
  
##  <a name="operator_eq"></a>CAtlFileMappingBase::operator =  
 将当前的文件映射对象设置为另一个文件映射对象。  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>参数  
 `orig`  
 当前的文件映射对象。  
  
### <a name="return-value"></a>返回值  
 返回与当前对象的引用。  
  
##  <a name="unmap"></a>CAtlFileMappingBase::Unmap  
 调用此方法来取消映射文件映射对象。  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 请参阅[UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的更多详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [CAtlFileMapping 类](../../atl/reference/catlfilemapping-class.md)   
 [类概述](../../atl/atl-class-overview.md)

