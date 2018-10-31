---
title: CDBErrorInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19daacae764d3cb5e6b6b24a8cae0516ff7fe352
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066573"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 类

支持使用 OLE DB 的 OLE DB 错误处理[IErrorRecords](/previous-versions/windows/desktop/ms718112)接口。

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
|[GetBasicErrorInfo](#getbasicerrorinfo)|调用[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)返回有关指定的错误的基本信息。|
|[GetCustomErrorObject](#getcustomerrorobject)|调用[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)上自定义错误对象返回到接口的指针。|
|[GetErrorInfo](#geterrorinfo)|调用[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)返回`IErrorInfo`到指定的记录的接口指针。|
|[GetErrorParameters](#geterrorparameters)|调用[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)返回错误参数。|
|[GetErrorRecords](#geterrorrecords)|获取指定对象的错误记录。|

## <a name="remarks"></a>备注

此接口向用户返回一个或多个错误记录。 调用[cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)第一，若要获取错误记录的计数。 然后调用访问的一个函数，如[cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)来检索为每个记录的错误信息。

## <a name="getallerrorinfo"></a> Cdberrorinfo:: Getallerrorinfo

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

#### <a name="parameters"></a>参数

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

如果成功，则为 S_OK。 请参阅[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)中*OLE DB 程序员参考*有关其他返回值。

### <a name="remarks"></a>备注

输出值*pbstrDescription*通过调用在内部获得`IErrorInfo::GetDescription`，这需要将值设置为 NULL，不支持区域设置，则以下条件都成立：

1. 值*lcid*不是美国英语和

1. 值*lcid*不是等于 GetUserDefaultLCID 返回的值。

## <a name="getbasicerrorinfo"></a> Cdberrorinfo:: Getbasicerrorinfo

调用[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)返回有关该错误，如返回代码和特定于提供程序的错误号的基本信息。

### <a name="syntax"></a>语法

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum, 
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>参数

请参阅[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="getcustomerrorobject"></a> Cdberrorinfo:: Getcustomerrorobject

调用[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)上自定义错误对象返回到接口的指针。

### <a name="syntax"></a>语法

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum, 
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>参数

请参阅[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="geterrorinfo"></a> Cdberrorinfo:: Geterrorinfo

调用[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)返回[IErrorInfo](/previous-versions/windows/desktop/ms718112)到指定的记录的接口指针。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum, 
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>参数

请参阅[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="geterrorparameters"></a> Cdberrorinfo:: Geterrorparameters

调用[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)返回错误参数。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum, 
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>参数

请参阅[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="geterrorrecords"></a> Cdberrorinfo:: Geterrorrecords

获取指定对象的错误记录。

### <a name="syntax"></a>语法

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk, 
   const IID& iid, 
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>参数

*pUnk*<br/>
[in]要为其获取错误记录对象的接口。

*iid*<br/>
[in]与错误关联的接口的 IID。

*pcRecords*<br/>
[out]指向 （一个基于） 中的错误记录数的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

如果你想要检查的接口，用于获取从错误的信息，请使用函数的第一种形式。 否则，请使用第二种形式。

## <a name="see-also"></a>请参阅

[DBViewer](../../visual-cpp-samples.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)