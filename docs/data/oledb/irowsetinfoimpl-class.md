---
title: IRowsetInfoImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9b784dbb13ff39be21ccd353d514dd244d5ae41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl 类
提供的实现[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IRowsetInfoImpl`。  
  
 `PropClass`  
 默认为可由用户定义的属性类`T`。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|返回行集所支持的所有属性的当前设置。|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|到书签所应用到的行集返回的接口指针。|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|返回创建下一个行集合的对象 （命令或会话） 上的接口指针。|  
  
## <a name="remarks"></a>备注  
 行集上的必需接口。 此类通过实现行集属性[属性集映射](../../data/oledb/begin-propset-map.md)命令类中定义。 若要使用命令类的属性集，将显示行集类，尽管命令或会话对象创建时其自己的副本运行时属性时，提供行集。  
  
## <a name="requirements"></a>要求  
 **标头：** altdb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)