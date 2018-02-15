---
title: "CUtlProps 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 291094cf913d9c64c91070a281968524227e1376
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cutlprops-class"></a>CUtlProps 类
实现各种不同的 OLE DB 属性接口属性 (例如， `IDBProperties`， `IDBProperties`，和`IRowsetInfo`)。  
  
## <a name="syntax"></a>语法

```cpp
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 包含的类`BEGIN_PROPSET_MAP`。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|获取来自属性集的属性。|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|用于设置属性之前验证值。|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|使用者在对象创建接口上调用方法时，请处理可选接口的请求。|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|设置要处理所链接的属性的属性后调用。|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|属性集中设置一个属性。|  
  
## <a name="remarks"></a>备注  
 此类大部分是实现详细信息。  
  
 `CUtlProps` 包含两个成员的内部设置属性： [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)和[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。  
  
 在属性集映射中使用的宏的详细信息，请参阅[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)和[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)