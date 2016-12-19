---
title: "IPersistPropertyBagImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPersistPropertyBagImpl"
  - "ATL.IPersistPropertyBagImpl<T>"
  - "ATL::IPersistPropertyBagImpl"
  - "ATL::IPersistPropertyBagImpl<T>"
  - "ATL.IPersistPropertyBagImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistPropertyBagImpl class"
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPersistPropertyBagImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 并允许对象保存其属性设置为一个由客户端提供的属性包。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template <   
class T   
>  
class ATL_NO_VTABLE IPersistPropertyBagImpl :  
public IPersistPropertyBag  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPersistPropertyBagImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IPersistPropertyBagImpl::GetClassID](../Topic/IPersistPropertyBagImpl::GetClassID.md)|检索对象的CLSID。|  
|[IPersistPropertyBagImpl::InitNew](../Topic/IPersistPropertyBagImpl::InitNew.md)|初始化新创建的对象。  ATL实现返回 `S_OK`。|  
|[IPersistPropertyBagImpl::Load](../Topic/IPersistPropertyBagImpl::Load.md)|从一个由客户端提供的属性包加载对象的属性。|  
|[IPersistPropertyBagImpl::Save](../Topic/IPersistPropertyBagImpl::Save.md)|保存对象的属性设置为一个由客户端提供的属性包。|  
  
## 备注  
 [IPersistPropertyBag](https://msdn.microsoft.com/en-us/library/aa768205.aspx) 接口允许对象保存其属性设置为一个由客户端提供的属性包。  选件类 `IPersistPropertyBagImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **IPersistPropertyBag** 与 [IPropertyBag](https://msdn.microsoft.com/en-us/library/aa768196.aspx) 和 [IErrorLog](https://msdn.microsoft.com/en-us/library/aa768231.aspx)协同工作。  必须由客户端实现后面这两个接口。  通过 `IPropertyBag`，客户端保存和加载对象的各个属性。  通过 **IErrorLog**，对象和客户端可能会遇到的任何错误。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [BEGIN\_PROP\_MAP](../Topic/BEGIN_PROP_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)