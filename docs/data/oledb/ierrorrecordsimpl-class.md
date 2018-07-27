---
title: IErrorRecordsImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a4f12bd935e7dedf46e531d46e2ec91084059e9d
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269681"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 类
实现 OLE DB [IErrorRecords](https://msdn.microsoft.com/library/ms718112.aspx)添加到记录且记录检索的数据成员的接口 ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 的类型**CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 一个类派生自`IErrorRecordsImpl`。  
  
 *RecordClass*  
 一个表示 OLE DB 错误对象的类。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetErrorDescriptionString](#geterrordescriptionstring)|获取从错误记录的错误描述字符串。|  
|[GetErrorGUID](#geterrorguid)|获取从错误记录错误的 GUID。|  
|[GetErrorHelpContext](#geterrorhelpcontext)|从错误记录中获取的帮助上下文 ID。|  
|[GetErrorHelpFile](#geterrorhelpfile)|获取错误记录的帮助文件的完整路径名。|  
|[GetErrorSource](#geterrorsource)|获取从错误记录错误的源代码。|  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[AddErrorRecord](#adderrorrecord)|将一条记录添加到 OLE DB 错误对象。|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|返回有关该错误，如返回代码和特定于提供程序的错误号的基本信息。|  
|[GetCustomErrorObject](#getcustomerrorobject)|返回一个指向接口上的自定义错误对象。|  
|[GetErrorInfo](#geterrorinfo)|返回[IErrorInfo](https://msdn.microsoft.com/library/ms718112.aspx)上指定的记录的接口指针。|  
|[GetErrorParameters](#geterrorparameters)|返回的错误参数。|  
|[GetRecordCount](#getrecordcount)|在 OLE DB 记录对象中返回记录的数。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_rgErrors](#rgerrors)|错误记录的数组。|  

## <a name="geterrordescriptionstring"></a> Ierrorrecordsimpl:: Geterrordescriptionstring
获取从错误记录的错误描述字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp
      LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>参数  
 *rCurError*  
 `ERRORINFO`中记录`IErrorInfo`接口。  
  
### <a name="return-value"></a>返回值  
 指向描述错误的字符串的指针。  
  
## <a name="geterrorguid"></a> Ierrorrecordsimpl:: Geterrorguid
获取从错误记录错误的 GUID。  
  
### <a name="syntax"></a>语法  
  
```cpp
      REFGUID GetErrorGUID(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>参数  
 *rCurError*  
 `ERRORINFO`中记录`IErrorInfo`接口。  
  
### <a name="return-value"></a>返回值  
 对错误的 GUID 的引用。  

## <a name="geterrorhelpcontext"></a> Ierrorrecordsimpl:: Geterrorhelpcontext
从错误记录中获取的帮助上下文 ID。  
  
### <a name="syntax"></a>语法  
  
```cpp
      DWORD GetErrorHelpContext(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>参数  
 *rCurError*  
 `ERRORINFO`中记录`IErrorInfo`接口。  
  
### <a name="return-value"></a>返回值  
 错误的帮助上下文 ID。  

## <a name="geterrorhelpfile"></a> Ierrorrecordsimpl:: Geterrorhelpfile
获取错误记录中的帮助文件的路径名称。  
  
### <a name="syntax"></a>语法  
  
```cpp
      LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>参数  
 *rCurError*  
 `ERRORINFO`中记录`IErrorInfo`接口。  
  
### <a name="return-value"></a>返回值  
 包含错误的帮助文件的路径名称的字符串指针。

## <a name="geterrorsource"></a> Ierrorrecordsimpl:: Geterrorsource
获取错误记录从导致了错误的源代码。  
  
### <a name="syntax"></a>语法  
  
```cpp
      LPOLESTR GetErrorSource(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>参数  
 *rCurError*  
 `ERRORINFO`中记录`IErrorInfo`接口。  
  
### <a name="return-value"></a>返回值  
 包含错误的源代码的字符串指针。 

## <a name="adderrorrecord"></a> Ierrorrecordsimpl:: Adderrorrecord
将一条记录添加到 OLE DB 错误对象。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,  
   DWORD dwLookupID,  
   DISPPARAMS *pdispparams,  
   IUnknown *punkCustomError,  
   DWORD dwDynamicErrorID);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::AddErrorRecord](https://msdn.microsoft.com/library/ms725362.aspx)中*OLE DB 程序员参考*。  

## <a name="getbasicerrorinfo"></a> Ierrorrecordsimpl:: Getbasicerrorinfo
返回有关该错误，如返回代码和特定于提供程序的错误号的基本信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,  
   ERRORINFO *pErrorInfo);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/library/ms723907.aspx)中*OLE DB 程序员参考*。 

## <a name="getcustomerrorobject"></a> Ierrorrecordsimpl:: Getcustomerrorobject
返回一个指向接口上的自定义错误对象。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,  
   REFIID riid,  
   IUnknown **ppObject);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/library/ms725417.aspx)中*OLE DB 程序员参考*。  

## <a name="geterrorinfo"></a> Ierrorrecordsimpl:: Geterrorinfo
返回[IErrorInfo](https://msdn.microsoft.com/library/ms718112.aspx)上指定的记录的接口指针。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,  
   LCID lcid,  
   IErrorInfo **ppErrorInfo);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/library/ms711230.aspx)中*OLE DB 程序员参考*。

## <a name="geterrorparameters"></a> Ierrorrecordsimpl:: Geterrorparameters
返回的错误参数。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,  
   DISPPARAMS *pdispparams);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/library/ms715793.aspx)中*OLE DB 程序员参考*。  

## <a name="getrecordcount"></a> Ierrorrecordsimpl:: Getrecordcount
在 OLE DB 记录对象中返回记录的数。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetRecordCount )(ULONG *pcRecords);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IErrorRecords::GetRecordCount](https://msdn.microsoft.com/library/ms722724.aspx)中*OLE DB 程序员参考*。  

## <a name="rgerrors"></a> Ierrorrecordsimpl:: M_rgerrors
错误记录的数组。  
  
### <a name="syntax"></a>语法  
  
```cpp
CAtlArray<  
RecordClass  
> m_rgErrors;  
  
```  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
