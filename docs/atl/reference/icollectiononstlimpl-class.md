---
title: "ICollectionOnSTLImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.ICollectionOnSTLImpl"
  - "ATL::ICollectionOnSTLImpl"
  - "ICollectionOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICollectionOnSTLImpl class"
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICollectionOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供集合选件类的方法。  
  
## 语法  
  
```  
  
      template <  
   class T,  
   class CollType,  
   class ItemType,  
   class CopyItem,  
   class EnumType  
>  
class ICollectionOnSTLImpl :  
   public T  
```  
  
#### 参数  
 `T`  
 COM集合接口。  
  
 `CollType`  
 STL容器选件类。  
  
 *ItemType*  
 容器接口显示的项的类型。  
  
 *CopyItem*  
 [复制策略类选件](../../atl/atl-copy-policy-classes.md)。  
  
 *EnumType*  
 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)与兼容的枚举数选件类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ICollectionOnSTLImpl::get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md)|返回集合中的enumerator对象。|  
|[ICollectionOnSTLImpl::get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md)|返回元素数集合中的。|  
|[ICollectionOnSTLImpl::get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md)|返回从集合的请求项。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[ICollectionOnSTLImpl::m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md)|集合。|  
  
## 备注  
 此选件类为集合接口的三种方法提供该实现: [get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md)、 [get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md)和 [get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md)。  
  
 使用此选件类:  
  
-   定义\(或借用\)要实现的集合接口。  
  
-   从 `ICollectionOnSTLImpl` 的专用化派生您的类选件基于此集合接口。  
  
-   使用您的派生类执行从 `ICollectionOnSTLImpl`不处理集合中的所有方法。  
  
> [!NOTE]
>  如果集合接口是双重接口，从 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)派生您的选件类，通过 `ICollectionOnSTLImpl` 专用化作为第一个模板参数，如果您希望ATL提供 `IDispatch` 方法的实现。  
  
-   将项目添加到 [m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md) 成员填充集合。  
  
 有关更多信息和示例，请参见 [ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## 继承层次结构  
 `T`  
  
 `ICollectionOnSTLImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [ATLCollections示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)