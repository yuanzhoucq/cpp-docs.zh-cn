---
title: "COleStreamFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
dev_langs:
- C++
helpviewer_keywords:
- data streams [C++]
- streams [C++], OLE
- data streams [C++], OLE
- structured storage in OLE
- OLE structured storage [C++]
- OLE [C++], streams of data
- COleStreamFile class
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0840d365f4179da0ad680256688eaf9484cb3cd8
ms.lasthandoff: 02/24/2017

---
# <a name="colestreamfile-class"></a>COleStreamFile 类
表示数据的流 ( `IStream`) 作为 OLE 结构化存储一部分的复合文件中。  
  
## <a name="syntax"></a>语法  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|构造 `COleStreamFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|将流与对象相关联。|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|从全局内存中创建一个流，并将其与对象相关联。|  
|[COleStreamFile::CreateStream](#createstream)|创建一个流，并将其与对象相关联。|  
|[COleStreamFile::Detach](#detach)|解除关联的流对象。|  
|[COleStreamFile::GetStream](#getstream)|返回当前的流。|  
|[COleStreamFile::OpenStream](#openstream)|安全地打开一个流，并将其与对象相关联。|  
  
## <a name="remarks"></a>备注  
 `IStorage`对象必须存在，然后才能打开或创建，除非它是一个内存流，该流。  
  
 `COleStreamFile`操作对象的完全类似[CFile](../../mfc/reference/cfile-class.md)对象。  
  
 有关操作流和存储的详细信息，请参阅文章[容器︰ 复合文件](../../mfc/containers-compound-files.md)...  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-nameattacha--colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Attach  
 将与所提供的 OLE 流相关联`COleStreamFile`对象。  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>参数  
 `lpStream`  
 指向 OLE 流 ( `IStream`) 要与对象相关联。 不能为**NULL**。  
  
### <a name="remarks"></a>备注  
 该对象已不得与 OLE 流相关联。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecolestreamfilea--colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 创建一个 `COleStreamFile` 对象。  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpStream`  
 OLE 流将与对象关联的指针。  
  
### <a name="remarks"></a>备注  
 如果`lpStream`是**NULL**、 对象不是与 OLE 流相关联，否则，该对象是与所提供的 OLE 流相关联。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatememorystreama--colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 安全地创建一个新流全局共享的内存不足其中失败是正常、 预期的条件。  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL** ，该值指示创建操作的完成状态。 如果您想要监视可能由于试图创建流产生的异常会提供此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建该流，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 由 OLE 子系统分配内存。  
  
 有关详细信息，请参阅[CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatestreama--colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream  
 安全地在其中失败是正常的预期情况提供的存储区对象中创建新的流。  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpStorage`  
 指向包含要创建的流的 OLE 存储对象。 不能为**NULL**。  
  
 `lpszStreamName`  
 要创建的流的名称。 不能为**NULL**。  
  
 `nOpenFlags`  
 在打开的流时要使用的访问模式。 排他锁，读/写，并创建模式默认情况下使用。 有关可用的模式的完整列表，请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL**。 如果您想要监视可能由于试图创建流产生的异常会提供此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建该流，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果打开失败，将引发文件例外和`pError`不是**NULL**。  
  
 有关详细信息，请参阅[IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedetacha--colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach  
 取消从对象的流关联而不关闭流。  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>返回值  
 写入流的指针 ( `IStream`) 这是与对象关联。  
  
### <a name="remarks"></a>备注  
 程序终止之前，必须以某种其他方式关闭流。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetstreama--colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream  
 调用此函数可将一个指针返回到当前流。  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前的流接口的指针 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034))。  
  
##  <a name="a-nameopenstreama--colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream  
 打开现有的流。  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpStorage`  
 指向包含要打开的流的 OLE 存储对象。 不能为**NULL**。  
  
 `lpszStreamName`  
 要打开的流的名称。 不能为**NULL**。  
  
 `nOpenFlags`  
 在打开的流时要使用的访问模式。 独占和读/写模式默认情况下使用。 有关可用的模式的完整列表，请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL**。 如果您想要监视可能由于试图打开流产生的异常会提供此参数。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则打开的流否则为 0。  
  
### <a name="remarks"></a>备注  
 如果打开失败，将引发文件例外和`pError`不是**NULL**。  
  
 有关详细信息，请参阅[IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




