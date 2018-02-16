---
title: "ISessionPropertiesImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISessionPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fafd303e6b03d5a78b11d9c6deb95233b082fd28
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 类
提供的实现[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`ISessionPropertiesImpl`。  
  
 `PropClass`  
 默认为可由用户定义的属性类`T`。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|返回当前会话设置会话属性组中的属性列表。|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|设置会话属性组属性。|  
  
## <a name="remarks"></a>备注  
 会话上的必需接口。 此类通过调用由定义的静态函数实现的会话属性[属性集映射](../../data/oledb/begin-propset-map.md)。 应在会话类中指定属性集映射。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)