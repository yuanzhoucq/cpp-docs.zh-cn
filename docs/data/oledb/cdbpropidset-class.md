---
title: "CDBPropIDSet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ee03feb715ebf96bd4de1af5374a2029f52bbf86
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet 类
继承自**DBPROPIDSET**结构并添加初始化键字段的构造函数以及[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)访问方法。  
  
## <a name="syntax"></a>语法

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|将属性添加到属性 ID 集。|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|构造函数。|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|设置属性 ID 集的 GUID。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cdbpropidset-operator-equal.md)|将属性 ID 集的内容分配到另一个属性 ID 集。|  
  
## <a name="remarks"></a>备注  
 OLE DB 使用者使用**DBPROPIDSET**结构传递使用者要为其获取属性信息的属性 Id 的数组。 在单个中标识的属性[DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx)结构属于一个属性集。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)