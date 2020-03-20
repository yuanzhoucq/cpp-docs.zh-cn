---
title: CDBErrorInfo 类
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: 2d2b21652fd5ee3604c3c72c2168c3d9a495caf1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546127"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 类

使用 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))接口为 OLE DB 错误处理提供支持。

## <a name="syntax"></a>语法

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|返回错误记录中包含的所有错误信息。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|调用[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))以返回有关指定错误的基本信息。|
|[GetCustomErrorObject](#getcustomerrorobject)|调用[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))以返回指向自定义错误对象上的接口的指针。|
|[GetErrorInfo](#geterrorinfo)|调用[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))以返回指定记录的 `IErrorInfo` 接口指针。|
|[GetErrorParameters](#geterrorparameters)|调用[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))以返回错误参数。|
|[GetErrorRecords](#geterrorrecords)|获取指定对象的错误记录。|

## <a name="remarks"></a>备注

此接口向用户返回一条或多条错误记录。 首先调用[CDBErrorInfo：： GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)以获取错误记录的计数。 然后调用某个访问函数（如[CDBErrorInfo：： GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)）来检索每条记录的错误信息。

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a>CDBErrorInfo：： GetAllErrorInfo

返回错误记录中包含的所有类型的错误信息。

### <a name="syntax"></a>语法

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>parameters

*ulRecordNum*<br/>
[in] 为其返回错误信息的记录的从零开始的数字。

*lcid*<br/>
[in] 要返回的错误信息的区域设置 ID。

*pbstrDescription*<br/>
[out] 当不支持区域设置时，指向错误或 NULL 的文本说明的指针。 请参阅“备注”。

*pbstrSource*<br/>
[out] 一个指针，该指针指向包含产生错误的组件的名称的字符串。

*pguid*<br/>
[out] 一个指针，该指针指向定义错误的接口的 GUID。

*pdwHelpContext*<br/>
[out] 指向错误的帮助上下文 ID 的指针。

*pbstrHelpFile*<br/>
[out] 一个指针，该指针指向包含描述错误的帮助文件的路径的字符串。

### <a name="return-value"></a>返回值

如果成功，则 S_OK。 有关其他返回值，请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

### <a name="remarks"></a>备注

*PbstrDescription*的输出值是通过调用 `IErrorInfo::GetDescription`（如果区域设置不受支持，则将值设置为 NULL），或者如果以下两个条件均为 true，则在内部获取：

1. *lcid*的值不是美国英语，

1. *lcid*的值不等于 GetUserDefaultLCID 返回的值。

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>CDBErrorInfo：： GetBasicErrorInfo

调用[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))以返回有关错误的基本信息，如返回代码和特定于提供程序的错误号。

### <a name="syntax"></a>语法

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a>CDBErrorInfo：： GetCustomErrorObject

调用[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))以返回指向自定义错误对象上的接口的指针。

### <a name="syntax"></a>语法

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a>CDBErrorInfo：： GetErrorInfo

调用[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))以将[IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))接口指针返回到指定的记录。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a>CDBErrorInfo：： GetErrorParameters

调用[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))以返回错误参数。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a>CDBErrorInfo：： GetErrorRecords

获取指定对象的错误记录。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>parameters

*pUnk*<br/>
中要为其获取错误记录的对象的接口。

*iid*<br/>
中与错误关联的接口的 IID。

*pcRecords*<br/>
弄一个指针，它指向错误记录的（从1开始）计数。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

如果要检查从中获取错误信息的接口，请使用第一种形式的函数。 否则，请使用第二个窗体。

## <a name="see-also"></a>另请参阅

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)