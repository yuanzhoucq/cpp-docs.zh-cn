---
title: "IPropertyNotifySinkCP 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: feff2467d6d72e9d0a9186dc269f48eb26cbfee2
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 类
此类公开[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)接口作为可连接对象上的传出接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPropertyNotifySinkCP`。  
  
 `CDV`  
 一个类，用于管理的连接点和其接收器之间的连接。 默认值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，它允许不受限制的连接。 您还可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定的数量的连接。  
  
## <a name="remarks"></a>备注  
 `IPropertyNotifySinkCP`继承其基类，通过的所有方法[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)接口允许接收有关属性更改通知接收器对象。 类`IPropertyNotifySinkCP`作为可连接对象上的传出接口公开此接口。 客户端必须实现`IPropertyNotifySink`接收器上的方法。  
  
 派生您的类从`IPropertyNotifySinkCP`如果想要创建连接点表示`IPropertyNotifySink`接口。  
  
 有关使用 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
## <a name="see-also"></a>另请参阅  
 [IConnectionPointImpl 类](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl 类](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

