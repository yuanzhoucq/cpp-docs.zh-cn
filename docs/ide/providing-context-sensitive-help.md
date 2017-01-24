---
title: "提供区分上下文的帮助 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "区分上下文的帮助"
  - "区分上下文的帮助, 自定义向导"
  - "自定义向导, 实现帮助"
ms.assetid: c6c4d961-29d3-4d16-9f39-b12545aba540
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供区分上下文的帮助
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当使用[自定义向导](../ide/application-settings-custom-wizard.md)创建向导时，它在向导上插入“帮助”按钮。  
  
 项目中的每个 .htm 文件均包含为向导提供“帮助”按钮支持的代码。  
  
```  
<BUTTON CLASS="BUTTONS" ID="HelpBtn" ACCESSKEY="H"  
 onClick="window.external.OnHelp('vc.appwiz.custom.overview');">  
```  
  
 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.OnHelp%2A> 指定与该向导页关联的 HTML 帮助文件的关键字。  有关创建与该页关联的 HTML 帮助文件的更多信息，请参见 [HTML 帮助起始页](vsconhh1start)。  若要为该向导页提供您自己的帮助，必须用标识该页的 HTML 帮助主题的关键字替换字符串 `'vc.appwiz.custom.overview'`。  
  
 **注意** 此 .htm 文件不能集成到已编译好的 MSDN 帮助中。  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)