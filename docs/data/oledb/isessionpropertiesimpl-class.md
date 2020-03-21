---
title: ISessionPropertiesImpl 类
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: c1a3539ea4ea705ad8bd1e40acda965ef66e2051
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077715"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 类

提供[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `ISessionPropertiesImpl`的类。

*PropClass*<br/>
用户可定义的属性类，默认值为*T*。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[GetProperties](#getproperties)|返回当前在会话中设置的会话属性组中的属性列表。|
|[SetProperties](#setproperties)|设置会话属性组中的属性。|

## <a name="remarks"></a>备注

会话上的必需接口。 此类通过调用由[属性集映射](../../data/oledb/begin-propset-map.md)定义的静态函数来实现会话属性。 应在会话类中指定属性集映射。

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a>ISessionPropertiesImpl：： GetProperties

返回当前在会话上设置 `DBPROPSET_SESSION` 属性组中的属性列表。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[ISessionProperties：： GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) 。

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a>ISessionPropertiesImpl：： SetProperties

设置 `DBPROPSET_SESSION` 属性组中的属性。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[ISessionProperties：： SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)