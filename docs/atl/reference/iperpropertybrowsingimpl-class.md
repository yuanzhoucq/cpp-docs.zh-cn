---
title: "IPerPropertyBrowsingImpl Class | Microsoft Docs"
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
  - "ATL.IPerPropertyBrowsingImpl"
  - "IPerPropertyBrowsing"
  - "ATL::IPerPropertyBrowsingImpl"
  - "ATL::IPerPropertyBrowsingImpl<T>"
  - "IPerPropertyBrowsingImpl"
  - "ATL.IPerPropertyBrowsingImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPerPropertyBrowsing, ATL 实现"
  - "IPerPropertyBrowsingImpl class"
  - "属性页, accessing information"
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPerPropertyBrowsingImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 并将客户端来访问对象中的属性页的信息。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :  
public IPerPropertyBrowsing  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPerPropertyBrowsingImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](../Topic/IPerPropertyBrowsingImpl::GetDisplayString.md)|检索描述特定属性的字符串。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](../Topic/IPerPropertyBrowsingImpl::GetPredefinedStrings.md)|检索字符串数组与特定属性可以接受的值相对应。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](../Topic/IPerPropertyBrowsingImpl::GetPredefinedValue.md)|检索包含属性的值 **VARIANT** 确定由特定的DISPID。  DISPID与从 `GetPredefinedStrings`检索的字符串名称。  ATL实现返回 **E\_NOTIMPL**。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](../Topic/IPerPropertyBrowsingImpl::MapPropertyToPage.md)|检索属性页的CLSID与给定属性。|  
  
## 备注  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432) 接口使客户端能够访问对象上的属性页的信息。  选件类 `IPerPropertyBrowsingImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
> [!NOTE]
>  如果您使用的是Microsoft Access作为容器应用程序，必须从 `IPerPropertyBrowsingImpl`派生您的选件类。  否则，Access不会加载您的控件。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IPropertyPageImpl Class](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)