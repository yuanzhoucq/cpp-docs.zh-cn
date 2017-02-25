---
title: "IPointerInactiveImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPointerInactiveImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inactive objects"
  - "IPointerInactive ATL implementation"
  - "IPointerInactiveImpl class"
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IPointerInactiveImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类执行 **IUnknown** 和 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) 接口方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IPointerInactiveImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPointerInactiveImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IPointerInactiveImpl::GetActivationPolicy](../Topic/IPointerInactiveImpl::GetActivationPolicy.md)|检索对象的当前激活策略。  ATL实现返回 **E\_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveMouseMove](../Topic/IPointerInactiveImpl::OnInactiveMouseMove.md)|通知对象鼠标指针移动了，它指示对象可以引发鼠标事件。  ATL实现返回 **E\_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveSetCursor](../Topic/IPointerInactiveImpl::OnInactiveSetCursor.md)|设置为非活动对象的鼠标指针。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 无事件对象是加载或运行的一个。  不同有效的对象，无事件对象无法接收Windows鼠标和键盘消息。  因此，非活动对象使用的资源是通常更为高效。  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) 接口允许对象支持鼠标交互的最低级别，在保持非活动任务时。  此功能为控件尤其有用。  
  
 通过返回 **E\_NOTIMPL**类别 `IPointerInactiveImpl` 实现 `IPointerInactive` 方法。  但是，它通过将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)