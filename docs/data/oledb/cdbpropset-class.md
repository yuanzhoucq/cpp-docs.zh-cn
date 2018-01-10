---
title: "CDBPropSet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b2523e37c3015bb49d123e99f39c1ea4bdb9045
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropset-class"></a>CDBPropSet 类
继承自**DBPROPSET**结构并添加初始化键字段的构造函数以及`AddProperty`访问方法。  
  
## <a name="syntax"></a>语法  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|将属性添加到属性集。|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|构造函数。|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|集**guidPropertySet**字段**DBPROPSET**结构。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](../../data/oledb/cdbpropset-operator-equal.md)|将分配一个属性设置为另一个的内容。|  
  
## <a name="remarks"></a>备注  
 OLE DB 提供程序和使用者使用**DBPROPSET**结构传递的数组`DBPROP`结构。 每个`DBPROP`结构表示一个属性，可以设置。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet 类](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET 结构](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [需要的 DBPROP 结构](https://msdn.microsoft.com/en-us/library/ms717970.aspx)