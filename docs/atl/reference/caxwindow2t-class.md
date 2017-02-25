---
title: "CAxWindow2T Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAxWindow2T<TBase>"
  - "ATL::CAxWindow2T"
  - "CAxWindow2T"
  - "ATL.CAxWindow2T<TBase>"
  - "ATL.CAxWindow2T"
  - "CAxWindow2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAxWindow2 class"
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CAxWindow2T Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于操作承载一个ActiveX控件的窗口提供方法，并为承载授权的ActiveX控件支持。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <   
class TBase= CWindow   
>  
class CAxWindow2T :   
public CAxWindowT< TBase >  
```  
  
#### 参数  
 *TBase*  
 `CAxWindowT` 派生的选件类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAxWindow2T::CAxWindow2T](../Topic/CAxWindow2T::CAxWindow2T.md)|构造 `CAxWindow2T` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAxWindow2T::Create](../Topic/CAxWindow2T::Create.md)|创建宿主窗口。|  
|[CAxWindow2T::CreateControlLic](../Topic/CAxWindow2T::CreateControlLic.md)|创建一个授权的ActiveX控件，将其初始化，并将其承载于指定的窗口。|  
|[CAxWindow2T::CreateControlLicEx](../Topic/CAxWindow2T::CreateControlLicEx.md)|创建一个授权的ActiveX控件，将其初始化，承载它在指定的窗口，然后从控件检索接口指针\(或指针）。|  
|[CAxWindow2T::GetWndClassName](../Topic/CAxWindow2T::GetWndClassName.md)|检索窗口选件类名称的静态方法。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAxWindow2T::operator \=](../Topic/CAxWindow2T::operator%20=.md)|分配 `HWND` 到现有的 `CAxWindow2T` 对象。|  
  
## 备注  
 `CAxWindow2T` 用于操作承载一个ActiveX控件的窗口的方法。  `CAxWindow2T` 还为承载授权的ActiveX控件支持。  “**AtlAxWinLic80**”提供承载，由 `CAxWindow2T`包装。  
  
 选件类 `CAxWindow2` 实现为 `CAxWindow2T` 选件类的专用化。  此专用化声明如下所示:  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
>  `CAxWindowT` 成员。[CAxWindow](../../atl/reference/caxwindow-class.md)下。  
  
 使用此选件类成员的示例 [承载使用ATL AXHost的ActiveX控件](../../atl/hosting-activex-controls-using-atl-axhost.md) 参见。  
  
## 继承层次结构  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [控件包含常见问题](../../atl/atl-control-containment-faq.md)