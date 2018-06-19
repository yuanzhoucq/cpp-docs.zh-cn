---
title: ICommandPropertiesImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25be1548bd41f832a007f102c138fc01f8818774
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098996"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 类
提供的实现[ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自  
  
 `PropClass`  
 属性类。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|返回在当前请求的行集的行集属性组的属性列表。|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|设置行集属性组属性。|  
  
## <a name="remarks"></a>备注  
 这是必需的对于命令。 由所定义的静态函数提供实现[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)宏。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)