---
title: "Adding Formatting or Special Characters to a String | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "special characters, adding to strings"
  - "ASCII characters, adding to strings"
  - "strings [C++], formatting"
  - "strings [C++], special characters"
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Formatting or Special Characters to a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 为字符串添加格式设置或特殊字符  
  
1.  双击[资源视图](../windows/resource-view-window.md)中的相应图标以打开字符串表。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  选择要修改的字符串。  
  
3.  在[“属性”窗口](../Topic/Properties%20Window.md)中，将下面列出的任意标准转义序列添加到“标题”框中的文本，并按 Enter。  
  
    |若要获得|请键入|  
    |----------|---------|  
    |换行|\\n|  
    |回车|\\r|  
    |Tab|\\t|  
    |反斜杠 \(\\\)|\\\\|  
    |ASCII 字符|\\ddd（八进制表示法）|  
    |提醒（铃声）|\\a|  
  
> [!NOTE]
>  字符串编辑器不支持全套的转义 ASCI 字符。  只能使用上面列出的 ASCII 字符。  
  
 有关将资源添加到托管项目（面向公共语言运行时的那些项目）的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [String Editor](../mfc/string-editor.md)   
 [字符串](_win32_Strings)   
 [关于字符串](_win32_About_Strings_cpp)