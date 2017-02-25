---
title: "Moving a String from One Resource File to Another | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], moving between files"
  - "resource script files, moving strings"
  - "string editing, moving strings between resources"
  - "String editor, moving strings between files"
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Moving a String from One Resource File to Another
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 在资源脚本文件之间移动字符串  
  
1.  打开两个 .rc 文件中的字符串表。  （有关更多信息，请参见[在项目外查看资源脚本文件中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。）  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  右击要移动的字符串，然后从快捷菜单中选择“剪切”。  
  
3.  将光标放在目标“字符串编辑器”窗口中。  
  
4.  在要将字符串移到的 .rc 文件中右击，然后从快捷菜单中选择“粘贴”。  
  
    > [!NOTE]
    >  如果被移动字符串的 **ID** 或 **value** 与目标文件中现有的 **ID** 或 **value** 冲突，被移动字符串的 **ID** 或 **value** 将更改。  如果存在具有相同 **ID** 的字符串，则被移动字符串的 **ID** 更改。  如果存在具有相同 **value** 的字符串，则被移动字符串的 **value** 更改。  
  
 有关将资源添加到托管项目（面向公共语言运行时的那些项目）的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [String Editor](../mfc/string-editor.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [自定义窗口布局](../Topic/Customizing%20window%20layouts%20in%20Visual%20Studio.md)   
 [字符串](_win32_Strings)   
 [关于字符串](_win32_About_Strings_cpp)