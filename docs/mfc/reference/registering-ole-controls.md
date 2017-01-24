---
title: "注册 OLE 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE 控件, 注册"
  - "注册 OLE 控件"
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
caps.latest.revision: 15
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 注册 OLE 控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 控件，例如其他与服务器对象，可由其他与识别应用程序访问。  这通过注册控件的类型库和类实现。  
  
 函数允许您添加和移除控件的类、属性页和窗口类型库注册的数据库：  
  
### 注册 OLE 控件  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](../Topic/AfxOleRegisterControlClass.md)|添加控件的类到注册数据库。|  
|[AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md)|将控件添加属性页到注册数据库。|  
|[AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md)|添加控件的类型库注册到数据库。|  
|[AfxOleUnregisterClass](../Topic/AfxOleUnregisterClass.md)|从注册数据库中移除控件类或属性页类。|  
|[AfxOleUnregisterTypeLib](../Topic/AfxOleUnregisterTypeLib.md)|从注册数据库中移除控件的类型库。|  
  
 `AfxOleRegisterTypeLib` 在 `DllRegisterServer`控件的实现 DLL 通常调用。  同样，`AfxOleUnregisterTypeLib` 是由 `DllUnregisterServer`调用。  `AfxOleRegisterControlClass`、`AfxOleRegisterPropertyPageClass`和 `AfxOleUnregisterClass` 由控件的类工厂或属性页的 `UpdateRegistry` 成员函数通常名为。  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)