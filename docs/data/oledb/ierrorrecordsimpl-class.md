---
title: IErrorRecordsImpl 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 40ac0b248e1e90dae29a787d59f6ded9581aca70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210595"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 类

实现 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))接口，将记录添加到**CAtlArray <** `RecordClass` **>** 的数据成员（[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)）中并从中检索记录。

## <a name="syntax"></a>语法

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IErrorRecordsImpl`的类。

*RecordClass*<br/>
表示 OLE DB 错误对象的类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|获取错误记录中的错误描述字符串。|
|[GetErrorGUID](#geterrorguid)|获取错误记录中的错误 GUID。|
|[GetErrorHelpContext](#geterrorhelpcontext)|从错误记录中获取帮助上下文 ID。|
|[GetErrorHelpFile](#geterrorhelpfile)|获取错误记录中帮助文件的完整路径名。|
|[GetErrorSource](#geterrorsource)|从错误记录获取错误源代码。|

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|向 OLE DB 错误对象添加记录。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|返回有关错误的基本信息，如返回代码和特定于提供程序的错误号。|
|[GetCustomErrorObject](#getcustomerrorobject)|返回一个指向自定义错误对象上的接口的指针。|
|[GetErrorInfo](#geterrorinfo)|返回指定记录上的[IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))接口指针。|
|[GetErrorParameters](#geterrorparameters)|返回错误参数。|
|[GetRecordCount](#getrecordcount)|返回 OLE DB 记录对象中的记录数。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_rgErrors](#rgerrors)|错误记录的数组。|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a>IErrorRecordsImpl：： GetErrorDescriptionString

获取错误记录中的错误描述字符串。

### <a name="syntax"></a>语法

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>parameters

*rCurError*<br/>
`IErrorInfo` 接口中的 `ERRORINFO` 记录。

### <a name="return-value"></a>返回值

指向描述错误的字符串的指针。

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a>IErrorRecordsImpl：： GetErrorGUID

获取错误记录中的错误 GUID。

### <a name="syntax"></a>语法

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>parameters

*rCurError*<br/>
`IErrorInfo` 接口中的 `ERRORINFO` 记录。

### <a name="return-value"></a>返回值

对错误的 GUID 的引用。

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a>IErrorRecordsImpl：： GetErrorHelpContext

从错误记录中获取帮助上下文 ID。

### <a name="syntax"></a>语法

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>parameters

*rCurError*<br/>
`IErrorInfo` 接口中的 `ERRORINFO` 记录。

### <a name="return-value"></a>返回值

错误的帮助上下文 ID。

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a>IErrorRecordsImpl：： GetErrorHelpFile

获取错误记录中帮助文件的路径名称。

### <a name="syntax"></a>语法

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>parameters

*rCurError*<br/>
`IErrorInfo` 接口中的 `ERRORINFO` 记录。

### <a name="return-value"></a>返回值

指向字符串的指针，该字符串包含错误的帮助文件的路径名称。

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a>IErrorRecordsImpl：： GetErrorSource

获取导致错误记录中的错误的源代码。

### <a name="syntax"></a>语法

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>parameters

*rCurError*<br/>
`IErrorInfo` 接口中的 `ERRORINFO` 记录。

### <a name="return-value"></a>返回值

指向包含错误源代码的字符串的指针。

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a>IErrorRecordsImpl：： AddErrorRecord

向 OLE DB 错误对象添加记录。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) 。

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>IErrorRecordsImpl：： GetBasicErrorInfo

返回有关错误的基本信息，如返回代码和特定于提供程序的错误号。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 。

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a>IErrorRecordsImpl：： GetCustomErrorObject

返回一个指向自定义错误对象上的接口的指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 。

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a>IErrorRecordsImpl：： GetErrorInfo

返回指定记录上的[IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a>IErrorRecordsImpl：： GetErrorParameters

返回错误参数。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 。

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a>IErrorRecordsImpl：： GetRecordCount

返回 OLE DB 记录对象中的记录数。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) 。

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a>IErrorRecordsImpl：： m_rgErrors

错误记录的数组。

### <a name="syntax"></a>语法

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
