---
title: "ICommandPropertiesImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs: C++
helpviewer_keywords: ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5878e7fa6345e294025b45474b1b384d01283c49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 类
提供的实现[ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx)接口。  
  
## <a name="syntax"></a>语法  
  
```  
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
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)