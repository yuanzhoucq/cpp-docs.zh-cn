---
title: CDBPropSet 类
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 08cab967fbfbd4b3207e96a4fdbd2d2dbc6da793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546115"
---
# <a name="cdbpropset-class"></a>CDBPropSet 类

从 `DBPROPSET` 结构继承，并添加初始化键字段和 `AddProperty` 访问方法的构造函数。

## <a name="syntax"></a>语法

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[AddProperty](#addproperty)|向属性集添加属性。|
|[CDBPropSet](#cdbpropset)|构造函数。|
|[SetGUID](#setguid)|设置 `DBPROPSET` 结构的 `guidPropertySet` 字段。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#op_equal)|将一个属性集的内容分配给另一个。|

## <a name="remarks"></a>备注

OLE DB 提供程序和使用者使用 `DBPROPSET` 结构来传递 `DBPROP` 结构的数组。 每个 `DBPROP` 结构都表示一个可以设置的属性。

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet：： AddProperty

向属性集添加属性。

### <a name="syntax"></a>语法

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>parameters

*dwPropertyID*<br/>
中要添加的属性的 ID。 用于初始化添加到属性集的 `DBPROP` 结构的 `dwPropertyID`。

*var*<br/>
中用于初始化添加到属性集的 `DBPROP` 结构的属性值的变量。

*szValue*<br/>
中用于初始化添加到属性集的 `DBPROP` 结构的属性值的字符串。

*bValue*<br/>
中一个 `BYTE` 或布尔值，该值用于初始化添加到属性集的 `DBPROP` 结构的属性值。

*N 值*<br/>
中一个整数值，用于初始化添加到属性集的 `DBPROP` 结构的属性值。

*fltValue*<br/>
中一个浮点值，该值用于初始化添加到属性集的 `DBPROP` 结构的属性值。

*dblValue*<br/>
中一个双精度浮点值，用于初始化添加到属性集的 `DBPROP` 结构的属性值。

*cyValue*<br/>
中一个 CY 货币值，该值用于初始化添加到属性集的 `DBPROP` 结构的属性值。

### <a name="return-value"></a>返回值

如果已成功添加属性，**则为 true** 。 否则为 **false**。

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet：： CDBPropSet

构造函数。 初始化[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的 `rgProperties`、`cProperties`和 `guidPropertySet` 字段。

### <a name="syntax"></a>语法

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中用于初始化 `guidPropertySet` 字段的 GUID。

*propset*<br/>
[in] 复制构造的另一个 `CDBPropSet` 对象。

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet：： SetGUID

设置 `DBPROPSET` 结构中的 `guidPropertySet` 字段。

### <a name="syntax"></a>语法

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中用于设置[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的 `guidPropertySet` 字段的 GUID。

### <a name="remarks"></a>备注

此字段也可以通过[构造函数](../../data/oledb/cdbpropset-cdbpropset.md)进行设置。

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet：： operator =

将一个属性集的内容分配给另一属性集。

### <a name="syntax"></a>语法

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 结构](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP 结构](/previous-versions/windows/desktop/ms717970(v=vs.85))