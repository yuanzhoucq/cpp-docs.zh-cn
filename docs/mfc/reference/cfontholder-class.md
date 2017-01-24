---
title: "CFontHolder Class | Microsoft Docs"
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
  - "CFontHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontHolder class"
  - "custom fonts"
  - "字体, ActiveX 控件"
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFontHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现常用字体属性并封装Windows字体对象和 `IFont` 接口的功能。  
  
## 语法  
  
```  
class CFontHolder  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFontHolder::CFontHolder](../Topic/CFontHolder::CFontHolder.md)|构造 `CFontHolder` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFontHolder::GetDisplayString](../Topic/CFontHolder::GetDisplayString.md)|检索容器中的属性浏览器显示的字符串。|  
|[CFontHolder::GetFontDispatch](../Topic/CFontHolder::GetFontDispatch.md)|返回字体的 `IDispatch` 接口。|  
|[CFontHolder::GetFontHandle](../Topic/CFontHolder::GetFontHandle.md)|返回的句柄。Windows字体。|  
|[CFontHolder::InitializeFont](../Topic/CFontHolder::InitializeFont.md)|初始化 `CFontHolder` 对象。|  
|[CFontHolder::QueryTextMetrics](../Topic/CFontHolder::QueryTextMetrics.md)|检索字体相关的信息。|  
|[CFontHolder::ReleaseFont](../Topic/CFontHolder::ReleaseFont.md)|从 `IFont` 和 `IFontNotification` 接口断开 `CFontHolder` 对象。|  
|[CFontHolder::Select](../Topic/CFontHolder::Select.md)|选择一种字体资源。设备上下文。|  
|[CFontHolder::SetFont](../Topic/CFontHolder::SetFont.md)|连接到 `IFont` 接口的 `CFontHolder` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CFontHolder::m\_pFont](../Topic/CFontHolder::m_pFont.md)|为 `CFontHolder` 对象的 `IFont` 接口的指针。|  
  
## 备注  
 `CFontHolder` 没有基类。  
  
 使用此选件类为控件实现自定义字体属性。  有关创建此类属性的信息，请参见文章 [ActiveX控件:使用字体](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
## 继承层次结构  
 `CFontHolder`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropExchange Class](../../mfc/reference/cpropexchange-class.md)