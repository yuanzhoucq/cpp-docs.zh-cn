---
title: "IQuickActivateImpl Class | Microsoft Docs"
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
  - "ATL::IQuickActivateImpl"
  - "ATL::IQuickActivateImpl<T>"
  - "ATL.IQuickActivateImpl"
  - "ATL.IQuickActivateImpl<T>"
  - "IQuickActivateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activating ATL controls"
  - "控件 [ATL], 激活"
  - "IQuickActivate ATL implementation"
  - "IQuickActivateImpl class"
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IQuickActivateImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类组合容器的控件初始化为一个调用。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template<   
class T   
>  
class ATL_NO_VTABLE IQuickActivateImpl :  
public IQuickActivate  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IQuickActivateImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IQuickActivateImpl::GetContentExtent](../Topic/IQuickActivateImpl::GetContentExtent.md)|检索正在运行的控件的当前显示范围。|  
|[IQuickActivateImpl::QuickActivate](../Topic/IQuickActivateImpl::QuickActivate.md)|执行加载的控件的快速初始化。|  
|[IQuickActivateImpl::SetContentExtent](../Topic/IQuickActivateImpl::SetContentExtent.md)|请注意控件要显示空间容器分配给它。|  
  
## 备注  
 [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) 界面帮助容器避免延迟，在加载控件将在单个时的初始化调用。  `QuickActivate` 方法允许容器通过指向存储指针为所有接口需要的 [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) 结构。  在回，控件通过指针保存指向其自己的接口，容器使用的 [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) 结构。  选件类 `IQuickActivateImpl` 提供 **IQuickActivate** 的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)