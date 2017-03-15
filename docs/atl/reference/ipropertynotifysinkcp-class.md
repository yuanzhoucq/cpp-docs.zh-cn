---
title: "IPropertyNotifySinkCP Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyNotifySinkCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "连接点 [C++], 管理"
  - "IPropertyNotifySinkCP class"
  - "sinks, notifying of changes"
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IPropertyNotifySinkCP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类公开 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 接口标记为可连接对象的一个输出接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      , class  
      CDV   
      = CComDynamicUnkArray >  
class IPropertyNotifySinkCP :   
public IConnectionPointImpl< T, &IID_IPropertyNotifySink, CDV>  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPropertyNotifySinkCP`。  
  
 `CDV`  
 管理之间的连接连接点的选件类及其接收器。  默认值为 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，允许无限制的连接。  还可以使用 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定连接的内置的数字。  
  
## 备注  
 `IPropertyNotifySinkCP` 通过其基类，[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)继承的所有方法。  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 接口允许接收器对象接收有关属性的更改通知。  选件类 `IPropertyNotifySinkCP` 显示此接口标记为可连接对象的一个输出接口。  客户端必须在该接收器的 `IPropertyNotifySink` 方法。  
  
 从 `IPropertyNotifySinkCP` 派生您的类选件，如果要创建表示 `IPropertyNotifySink` 接口的连接点时。  
  
 有关使用的更多信息在ATL连接点，请参见一 [连接点](../../atl/atl-connection-points.md)文章。  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IConnectionPointImpl Class](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl Class](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)