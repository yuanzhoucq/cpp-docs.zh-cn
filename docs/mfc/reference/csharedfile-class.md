---
title: "CSharedFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs: C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27c749f86f9e3fbd310fd03b3a82768d58632087
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CSharedFile::Detach](#detach)|关闭的共享的内存文件，并返回其内存块的句柄。|  
|[CSharedFile::SetHandle](#sethandle)|将共享的内存文件附加到的内存块。|  
  
## <a name="remarks"></a>备注  
 内存文件行为类似于磁盘文件，只不过该文件存储在 RAM 中，而不是在磁盘上。 内存文件可用于快速临时存储或传输原始字节或序列化的独立进程之间的对象。  
  
 从其他内存文件不同的共享的内存文件，因为它们的内存分配与[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函数。 `CSharedFile`类将数据存储在全局范围内分配的内存块 (使用创建**GlobalAlloc**)，并可以使用 DDE、 剪贴板或其他 OLE/COM 统一数据传输操作，例如，共享该内存块使用`IDataObject`。  
  
 **GlobalAlloc**返回`HGLOBAL`处理而不是指向内存，如通过返回的指针的指针[malloc](../../c-runtime-library/reference/malloc.md)。 `HGLOBAL`句柄需要在某些应用程序。 例如，若要将数据放在剪贴板需要`HGLOBAL`处理。  
  
 请注意，`CSharedFile`不使用内存映射文件，和数据不能直接共享进程间。  
  
 `CSharedFile`对象可以自动分配其自己的内存，或者可以将附加到你自己内存块`CSharedFile`对象通过调用[CSharedFile::SetHandle](#sethandle)。 在任一情况下，为自动增长的内存文件的内存分配中`nGrowBytes`-如果大小为增量`nGrowBytes`不为零。  
  
 有关详细信息，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxadv.h  
  
##  <a name="csharedfile"></a>CSharedFile::CSharedFile  
 构造`CSharedFile`对象，并为其分配内存。  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>参数  
 *nAllocFlags*  
 标志，指示内存的分配方式。 请参阅[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)有关有效的标志值的列表。  
  
 `nGrowBytes`  
 以字节为单位的内存分配增量。  
  
##  <a name="detach"></a>CSharedFile::Detach  
 调用此函数会关闭内存文件并将其与内存块分离。  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>返回值  
 包含内存文件的内容的内存块的句柄。  
  
### <a name="remarks"></a>备注  
 你可以通过调用重新打开它[SetHandle](#sethandle)，使用返回的句柄**分离**。  
  
##  <a name="sethandle"></a>CSharedFile::SetHandle  
 调用此函数可将附加到的全局内存块`CSharedFile`对象。  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *hGlobalMemory*  
 要附加到的全局内存的句柄`CSharedFile`。  
  
 `bAllowGrow`  
 指定是否允许的内存块增长。  
  
### <a name="remarks"></a>备注  
 如果`bAllowGrow`不为零，增加了大小的内存块根据需要，例如，如果尝试进行多个字节写入文件比已分配的内存块。  
  
## <a name="see-also"></a>请参阅  
 [CMemFile 类](../../mfc/reference/cmemfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMemFile 类](../../mfc/reference/cmemfile-class.md)
