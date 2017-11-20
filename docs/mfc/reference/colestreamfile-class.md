---
title: "COleStreamFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs: C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c7b9e26013a505f5de137797964ed19376569a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="colestreamfile-class"></a>COleStreamFile 类
表示数据的流 ( `IStream`) 作为 OLE 结构化存储一部分的复合文件中。  
  
## <a name="syntax"></a>语法  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|构造 `COleStreamFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|将流与对象相关联。|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|从全局内存中创建一个流，并将其关联的对象。|  
|[COleStreamFile::CreateStream](#createstream)|创建一个流，并将其关联的对象。|  
|[COleStreamFile::Detach](#detach)|解除关联的流对象。|  
|[COleStreamFile::GetStream](#getstream)|返回当前的流。|  
|[COleStreamFile::OpenStream](#openstream)|安全地打开一个流，并将其关联的对象。|  
  
## <a name="remarks"></a>备注  
 `IStorage`之前流可以打开或创建，除非它是一个内存流对象必须存在。  
  
 `COleStreamFile`操作对象的完全相同[CFile](../../mfc/reference/cfile-class.md)对象。  
  
 有关操作流与存储的详细信息，请参阅文章[容器： 复合文件](../../mfc/containers-compound-files.md)...  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="attach"></a>COleStreamFile::Attach  
 将与所提供的 OLE 流相关联`COleStreamFile`对象。  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>参数  
 `lpStream`  
 指向 OLE 流 ( `IStream`) 与对象相关联。 不能为**NULL**。  
  
### <a name="remarks"></a>备注  
 对象已不得与 OLE 流相关联。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 创建一个 `COleStreamFile` 对象。  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpStream`  
 指向要将与对象相关联的 OLE 流指针。  
  
### <a name="remarks"></a>备注  
 如果`lpStream`是**NULL**、 对象不是与 OLE 流关联，否则，该对象是与提供的 OLE 流相关联。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 安全地创建一个新流全局、 共享内存不足其中故障为正常，预期的条件。  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL** ，该值指示创建操作的完成状态。 如果你想要监视可能尝试创建流的生成的异常，请提供此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建流则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 OLE 子系统分配内存。  
  
 有关详细信息，请参阅[CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) Windows SDK 中。  
  
##  <a name="createstream"></a>COleStreamFile::CreateStream  
 安全地在其中的失败问题是正常，预期的条件所提供的存储对象中创建一个新的流。  
  
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
 打开流时要使用的访问模式。 独占，读/写和创建模式默认情况下使用。 有关可用的模式的完整列表，请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL**。 如果你想要监视可能尝试创建流的生成的异常，请提供此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建流则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 如果打开失败，则将引发文件异常和`pError`不**NULL**。  
  
 有关详细信息，请参阅[IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) Windows SDK 中。  
  
##  <a name="detach"></a>COleStreamFile::Detach  
 解除对象的流未关闭流之间的关联。  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向流的指针 ( `IStream`) 这是与对象关联。  
  
### <a name="remarks"></a>备注  
 在程序终止之前，必须以某种其他方式关闭流。  
  
 有关详细信息，请参阅[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) Windows SDK 中。  
  
##  <a name="getstream"></a>COleStreamFile::GetStream  
 调用此函数可将指针返回到当前流。  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前的流接口的指针 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034))。  
  
##  <a name="openstream"></a>COleStreamFile::OpenStream  
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
 打开流时要使用的访问模式。 独占和读/写模式默认情况下使用。 有关可用的模式的完整列表，请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。  
  
 `pError`  
 指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或**NULL**。 如果你想要监视可能由尝试打开流生成的异常，请提供此参数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打开流，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果打开失败，则将引发文件异常和`pError`不**NULL**。  
  
 有关详细信息，请参阅[IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) Windows SDK 中。  
  
## <a name="see-also"></a>另请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



