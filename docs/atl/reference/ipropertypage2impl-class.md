---
title: "IPropertyPage2Impl Class | Microsoft Docs"
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
  - "IPropertyPage2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage2 ATL implementation"
  - "IPropertyPage2Impl class"
  - "属性页"
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPropertyPage2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 和继承 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPage2Impl : public IPropertyPageImpl< T>  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPropertyPage2Impl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IPropertyPage2Impl::EditProperty](../Topic/IPropertyPage2Impl::EditProperty.md)|指定哪个属性控件将接收焦点，当激活属性页。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) 接口通过添加 `EditProperty` 方法扩展 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)。  此方法允许客户端选择在属性页中对象的特定属性。  
  
 选件类 `IPropertyPage2Impl` 返回 **IPropertyPage2::EditProperty**的 **E\_NOTIMPL**。  但是，它继承 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) 的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 当您创建属性页时，您的选件类从 `IPropertyPageImpl`通常派生。  若要提供额外支持 **IPropertyPage2**，修改您的类定义并重写 `EditProperty` 方法。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)