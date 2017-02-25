---
title: "IPropertyPageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage ATL implementation"
  - "IPropertyPageImpl class"
  - "属性页"
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 并提供 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 接口的默认实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPageImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPropertyPageImpl`。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[IPropertyPageImpl::IPropertyPageImpl](../Topic/IPropertyPageImpl::IPropertyPageImpl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IPropertyPageImpl::Activate](../Topic/IPropertyPageImpl::Activate.md)|创建属性页的对话框窗口。|  
|[IPropertyPageImpl::Apply](../Topic/IPropertyPageImpl::Apply.md)|将当前页属性值应用于通过 `SetObjects`指定的基础对象。  ATL实现返回 `S_OK`。|  
|[IPropertyPageImpl::Deactivate](../Topic/IPropertyPageImpl::Deactivate.md)|销毁用 **Activate**创建的窗口。|  
|[IPropertyPageImpl::GetPageInfo](../Topic/IPropertyPageImpl::GetPageInfo.md)|检索有关属性页的信息。|  
|[IPropertyPageImpl::Help](../Topic/IPropertyPageImpl::Help.md)|调用属性页的Windows帮助。|  
|[IPropertyPageImpl::IsPageDirty](../Topic/IPropertyPageImpl::IsPageDirty.md)|指示属性页是否已更改，则激活为。|  
|[IPropertyPageImpl::Move](../Topic/IPropertyPageImpl::Move.md)|位置和大小调整属性页"对话框。|  
|[IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)|标记未更改的属性页的状态为已更改或。|  
|[IPropertyPageImpl::SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|为对象提供一组 **IUnknown** 指针与属性页。  这些对象是通过调用接收当前页属性值设置为 **Apply**。|  
|[IPropertyPageImpl::SetPageSite](../Topic/IPropertyPageImpl::SetPageSite.md)|提供属性页。`IPropertyPageSite` 指针，属性页与属性框架通信。|  
|[IPropertyPageImpl::Show](../Topic/IPropertyPageImpl::Show.md)|使属性页"对话框显示或不可见。|  
|[IPropertyPageImpl::TranslateAccelerator](../Topic/IPropertyPageImpl::TranslateAccelerator.md)|处理一个指定的键击。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[IPropertyPageImpl::m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md)|指定属性页的状态是否已更改。|  
|[IPropertyPageImpl::m\_dwDocString](../Topic/IPropertyPageImpl::m_dwDocString.md)|存储资源标识符与描述属性页上的文本字符串。|  
|[IPropertyPageImpl::m\_dwHelpContext](../Topic/IPropertyPageImpl::m_dwHelpContext.md)|存储帮助主题的上下文标识符与属性页。|  
|[IPropertyPageImpl::m\_dwHelpFile](../Topic/IPropertyPageImpl::m_dwHelpFile.md)|存储资源标识符与描述属性页的帮助文件的名称。|  
|[IPropertyPageImpl::m\_dwTitle](../Topic/IPropertyPageImpl::m_dwTitle.md)|存储资源标识符与显示在属性页的选项卡上的文本字符串。|  
|[IPropertyPageImpl::m\_nObjects](../Topic/IPropertyPageImpl::m_nObjects.md)|存储对象的数量与属性页。|  
|[IPropertyPageImpl::m\_pPageSite](../Topic/IPropertyPageImpl::m_pPageSite.md)|指向 `IPropertyPageSite` 属性页与属性框架通信的接口。|  
|[IPropertyPageImpl::m\_ppUnk](../Topic/IPropertyPageImpl::m_ppUnk.md)|指向数组 **IUnknown** 指向对象与属性页。|  
|[IPropertyPageImpl::m\_size](../Topic/IPropertyPageImpl::m_size.md)|在像素存储属性页"对话框的高度和宽度。|  
  
## 备注  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 接口允许对象管理在属性表中的特定属性页。  选件类 `IPropertyPageImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IPropertyPage2Impl Class](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)