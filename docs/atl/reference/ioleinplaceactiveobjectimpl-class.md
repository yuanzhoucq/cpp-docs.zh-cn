---
title: "IOleInPlaceActiveObjectImpl Class | Microsoft Docs"
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
  - "IOleInPlaceActiveObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], communication between container and control"
  - "IOleInPlaceActiveObject, ATL 实现"
  - "IOleInPlaceActiveObjectImpl class"
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
caps.latest.revision: 22
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleInPlaceActiveObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于协助一个就地控件与其容器之间的通信的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IOleInPlaceActiveObjectImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IOleInPlaceActiveObjectImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](../Topic/IOleInPlaceActiveObjectImpl::ContextSensitiveHelp.md)|启用区分上下文的帮助。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](../Topic/IOleInPlaceActiveObjectImpl::EnableModeless.md)|启用无模式对话框。  ATL实现返回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::GetWindow](../Topic/IOleInPlaceActiveObjectImpl::GetWindow.md)|获取窗口句柄。|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnDocWindowActivate.md)|在容器的文档窗口中激活或停用时，请注意控件。  ATL实现返回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnFrameWindowActivate.md)|激活时，容器顶部框架窗口或停用时，请注意控件。  ATL实现返回|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](../Topic/IOleInPlaceActiveObjectImpl::ResizeBorder.md)|通知它需要调整其边框的控件。  ATL实现返回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](../Topic/IOleInPlaceActiveObjectImpl::TranslateAccelerator.md)|处理菜单从容器的快捷键按键消息。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) 接口帮助一个就地控件与其容器之间的通信;例如，将控件和容器的活动状态和通知该控件需要调整自身。  选件类 `IOleInPlaceActiveObjectImpl` 提供 `IOleInPlaceActiveObject` 的默认实现并将信息发送支持 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)