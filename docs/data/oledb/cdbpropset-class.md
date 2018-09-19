---
title: CDBPropSet 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6d62b8d4b033d1b90c753d5de1752f0cb737f0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114652"
---
# <a name="cdbpropset-class"></a>CDBPropSet 类

继承自`DBPROPSET`结构，并添加初始化键字段的构造函数并将`AddProperty`访问方法。  
  
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
|[AddProperty](#addproperty)|将属性添加到属性集。|  
|[CDBPropSet](#cdbpropset)|构造函数。|  
|[SetGUID](#setguid)|集`guidPropertySet`字段的`DBPROPSET`结构。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](#op_equal)|将分配设置为另一个属性的内容。|  
  
## <a name="remarks"></a>备注  

OLE DB 提供程序和使用者使用`DBPROPSET`结构传递的数组`DBPROP`结构。 每个`DBPROP`结构表示可以设置的单个属性。  

## <a name="addproperty"></a> Cdbpropset:: Addproperty

将属性添加到属性集。  
  
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
  
#### <a name="parameters"></a>参数  

*dwPropertyID*<br/>
[in]要添加的属性 ID。 用来初始化`dwPropertyID`的`DBPROP`结构添加到属性集。  
  
*var*<br/>
[in]用于初始化的属性值的变体`DBPROP`结构添加到属性集。  
  
*szValue*<br/>
[in]用于初始化的属性值的字符串`DBPROP`结构添加到属性集。  
  
*其中 bValue*<br/>
[in]一个`BYTE`或用来初始化的属性值的布尔值`DBPROP`结构添加到属性集。  
  
*n 值*<br/>
[in]用于初始化的属性值的整数值`DBPROP`结构添加到属性集。  
  
*fltValue*<br/>
[in]用于初始化的属性值的浮点值`DBPROP`结构添加到属性集。  
  
*dblValue*<br/>
[in]用于初始化的属性值的双精度浮点值`DBPROP`结构添加到属性集。  
  
*cyValue*<br/>
[in]用于初始化的属性值的 CY 货币值`DBPROP`结构添加到属性集。  
  
### <a name="return-value"></a>返回值  

**true**如果属性已成功添加。 否则为**false**。 

## <a name="cdbpropset"></a> Cdbpropset:: Cdbpropset

构造函数。 初始化`rgProperties`， `cProperties`，并`guidPropertySet`的字段[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))结构。  
  
### <a name="syntax"></a>语法  
  
```cpp
CDBPropSet(const GUID& guid);  

CDBPropSet(const CDBPropSet& propset);  

CDBPropSet();  
```  
  
#### <a name="parameters"></a>参数  

*guid*<br/>
[in]使用 GUID 来初始化`guidPropertySet`字段。  
  
*propset*<br/>
[in] 复制构造的另一个 `CDBPropSet` 对象。  

## <a name="setguid"></a> Cdbpropset:: Setguid

集`guidPropertySet`字段中`DBPROPSET`结构。  
  
### <a name="syntax"></a>语法  
  
```cpp
void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>参数  

*guid*<br/>
[in]使用 GUID 来设置`guidPropertySet`字段[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))结构。  
  
### <a name="remarks"></a>备注  

可设置此字段[构造函数](../../data/oledb/cdbpropset-cdbpropset.md)也。  

## <a name="op_equal"></a> Cdbpropset:: Operator =

将一个属性集的内容分配给另一属性集。  
  
### <a name="syntax"></a>语法  
  
```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();  
```  
  
## <a name="see-also"></a>请参阅  

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 结构](/previous-versions/windows/desktop/ms714367\(v=vs.85\))   
[DBPROP 结构](/previous-versions/windows/desktop/ms717970\(v=vs.85\))