---
title: "将向导本地化为多种语言 | Microsoft Docs"
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
  - "自定义向导, 本地化"
  - "全球化 [C++], 向导"
  - "本地化 [C++], 向导"
  - "向导 [C++], 本地化"
ms.assetid: 879885c2-fafd-44fd-8032-bf0c301f4f45
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将向导本地化为多种语言
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以用 Visual Studio 提供支持的任何语言创建向导。  默认情况下，当安装 Visual Studio 时，它从注册表识别区域设置并为该区域设置提供适当的模板。  
  
 Visual Studio 使用语言 ID 识别向导需要的语言支持。  默认情况下，语言 ID 设置为注册表项 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage 的十进制值。  如果向导未找到语言项，则默认为英语 \(1033\)。  
  
> [!NOTE]
>  有关十进制语言值的列表，请参见[其他语言的向导支持](../ide/wizard-support-for-other-languages.md)。  
  
 语言 ID 被指定为 [HTML 文件](../ide/html-files.md)和[模板文件](../ide/template-files.md)所驻留路径内的 [vsz 文件](../Topic/Configuring%20.Vsz%20Files%20to%20Start%20Wizards.md)中的自定义参数。  
  
 应指定提供的 .htm 文件所使用的每种语言的路径。  
  
## 示例  
 设置 .vsz 文件中的下列自定义参数，以指示所提供的 HTML 使用的是英语 \(1033\)、日语 \(1041\) 还是德语 \(1031\)：  
  
```  
Param="START_PATH\HTML\1033"  
Param="START_PATH\HTML\1041"  
Param="START_PATH\HTML\1031"  
Param="START_PATH\Templates\1033"  
Param="START_PATH\Templates\1041"  
Param="START_PATH\Templates\1031"  
```  
  
 设置以上自定义参数将建立如下所示的向导目录结构：  
  
```  
MyWizard1  
   HTML  
      1033  
         default.htm  
         myEnglishHTML.htm  
      1041  
         default.htm  
         myJapaneseHTML.htm  
      1031  
         default.htm  
         myGermanHTML.htm  
   Templates  
      1033  
         stdafx.h  
         stdafx.cpp  
      1041  
         stdafx.h  
         stdafx.cpp  
      1031  
         stdafx.h  
         stdafx.cpp  
   Images  
      HtmlPage1.bmp  
      HtmlPage2.jpg  
   Scripts  
      Default.js  
```  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [向导 .Vsz 文件中的自定义参数](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)