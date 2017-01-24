---
title: "Adding or Deleting a String | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], adding to string tables"
  - "string tables, deleting strings"
  - "strings [C++], deleting in string tables"
  - "string tables, adding strings"
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding or Deleting a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用字符串编辑器可以快速地将新项插入到字符串表中。  新字符串放在表的最后，并且具有下一个可用的标识符。  然后可以在[“属性”窗口](../Topic/Properties%20Window.md)中根据需要编辑“标识”、“值”或“标题”属性。  
  
 字符串编辑器确保您不会使用已在使用的 ID。  如果选择的 ID 已在使用，字符串编辑器将通知您，然后分配一个一般的唯一 ID，例如 IDS\_STRING58113。  
  
### 添加字符串表项  
  
1.  双击[资源视图](../windows/resource-view-window.md)中的相应图标以打开字符串表。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在字符串表中右击，然后从快捷菜单中选择“新建字符串”。  
  
3.  在**字符串**编辑器中，从 ID 下拉列表中选择 **ID** 或就地直接键入 ID。  
  
4.  如有必要，编辑**“值”**。  
  
5.  键入“标题”的项。  
  
    > [!NOTE]
    >  在 Windows 字符串表中不允许有空字符串。  如果在字符串表中创建的项是空字符串，则将收到一条请求消息：“请输入该表项的字符串”。  
  
### 删除字符串表项  
  
1.  选择要删除的项。  
  
2.  在**“编辑”**菜单上，单击**“删除”**。  
  
 \- 或 \-  
  
-   右击要删除的字符串，然后从快捷菜单中选择“删除”。  
  
 \- 或 \-  
  
-   按 **Delete** 键。  
  
 有关将资源添加到托管项目（面向公共语言运行时的那些项目）的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [String Editor](../mfc/string-editor.md)   
 [字符串](_win32_Strings)   
 [关于字符串](_win32_About_Strings_cpp)