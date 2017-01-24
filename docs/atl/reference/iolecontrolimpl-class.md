---
title: "IOleControlImpl Class | Microsoft Docs"
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
  - "IOleControlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleControlImpl class"
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleControlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 **IOleControl** 接口的默认实现\)和实现 **IUnknown**。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IOleControlImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IOleControlImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IOleControlImpl::FreezeEvents](../Topic/IOleControlImpl::FreezeEvents.md)|指示容器是否忽略或接受来自控件的事件。|  
|[IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)|有关填充控件的键盘行为的信息。  ATL实现返回 **E\_NOTIMPL**。|  
|[IOleControlImpl::OnAmbientPropertyChange](../Topic/IOleControlImpl::OnAmbientPropertyChange.md)|通知一个控件的一个或多个容器的单个属性已更改。  ATL实现返回 `S_OK`。|  
|[IOleControlImpl::OnMnemonic](../Topic/IOleControlImpl::OnMnemonic.md)|请注意控件用户按下了一个指定的键击。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 选件类 `IOleControlImpl` 提供 [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) 接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IOleObjectImpl Class](../../atl/reference/ioleobjectimpl-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)