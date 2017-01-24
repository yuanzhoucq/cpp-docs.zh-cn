---
title: "类工厂和许可 | Microsoft Docs"
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
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类工厂, 和授权"
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 类工厂和许可
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建 OLE 控件的实例，容器应用程序调用控件的类工厂的成员函数。  由于控件是实际 OLE 对象，工厂类负责创建控件的实例。  OLE 每个控件类必须有一类工厂。  
  
 OLE 控件另一个重要功能是能够强制执行许可证。  ControlWizard 可以在控件创建项目时将授权。  有关授权已创建的 ActiveX 控件的更多信息，请参见[授权 ActiveX 控件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
 下表列出用于中的多个宏和函数声明和实现控件的类工厂并为控件的许可证。  
  
### 类工厂和许可  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE\_EX](../Topic/DECLARE_OLECREATE_EX.md)|声明一个 OLE 控件或属性页的类工厂。|  
|[IMPLEMENT\_OLECREATE\_EX](../Topic/IMPLEMENT_OLECREATE_EX.md)|实现控件的 `GetClassID` 函数并声明工厂类的实例。|  
|[BEGIN\_OLEFACTORY](../Topic/BEGIN_OLEFACTORY.md)|开始任何授权函数的声明。|  
|[END\_OLEFACTORY](../Topic/END_OLEFACTORY.md)|结束任何授权函数的声明。|  
|[AfxVerifyLicFile](../Topic/AfxVerifyLicFile.md)|验证控件中是否允许为在特定计算机上使用。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)