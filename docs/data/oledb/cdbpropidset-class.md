---
title: CDBPropIDSet 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5e77b92822ac82a4fbea06fe354952c9dbd79378
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207580"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 类
继承自`DBPROPIDSET`结构，并添加初始化键字段的构造函数并将[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)访问方法。  
  
## <a name="syntax"></a>语法

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  

## <a name="requirements"></a>要求  
 **标头:** atldbcli.h
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddPropertyID](#addpropertyid)|将属性添加到属性 ID 集。|  
|[CDBPropIDSet](#cdbpropidset)|构造函数。|  
|[SetGUID](#setguid)|设置属性 ID 集的 GUID。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](#op_equal)|将属性 ID 集的内容分配到另一个属性 ID 集。|  
  
## <a name="remarks"></a>备注  
 OLE DB 使用者使用`DBPROPIDSET`结构传递的使用者要为其获取属性信息的属性 Id 的数组。 在单个标识的属性[DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx)结构属于一个属性集。  

## <a name="addpropertyid"></a> Cdbpropidset:: Addpropertyid
将属性 ID 添加到属性 ID 集中。  
  
### <a name="syntax"></a>语法  
  
```cpp
      bool AddPropertyID(DBPROPID propid) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *propid*  
 [in] 要添加到属性 ID 集中的属性 ID。  

## <a name="cdbpropidset"></a> Cdbpropidset:: Cdbpropidset
构造函数。 初始化`rgProperties`， `cProperties`，和 （可选）`guidPropertySet`的字段[DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx)结构。  
  
### <a name="syntax"></a>语法  
  
```cpp
      CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 [in]使用 GUID 来初始化`guidPropertySet`字段。  
  
 *propidset*  
 [in] 复制构造的另一个 `CDBPropIDSet` 对象。  

## <a name="setguid"></a> Cdbpropidset:: Setguid
GUID 字段设置`DBPROPIDSET`结构。  
  
### <a name="syntax"></a>语法  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *guid*  
 [in]使用 GUID 来设置`guidPropertySet`字段[DBPROPIDSET](https://msdn.microsoft.com/library/ms717981.aspx)结构。  
  
### <a name="remarks"></a>备注  
 可设置此字段[构造函数](../../data/oledb/cdbpropidset-cdbpropidset.md)也。 如果您对此类使用默认构造函数，则调用此函数。  

## <a name="op_equal"></a> Cdbpropidset:: Operator =
将一个属性 ID 集的内容分配给另一 ID 属性集。  
  
### <a name="syntax"></a>语法  
  
```cpp
      CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();  
```  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)