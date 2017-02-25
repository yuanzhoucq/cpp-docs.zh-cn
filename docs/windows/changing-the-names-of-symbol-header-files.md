---
title: "Changing the Names of Symbol Header Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing.header"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource files, multiple"
  - "Resource Includes dialog box"
  - "symbol header files, changing names"
  - "symbol header files"
  - "header files, changing names"
  - "names [C++], symbol header files"
  - "symbols, symbol header files"
  - "Resource.h"
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Changing the Names of Symbol Header Files
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常情况下所有符号定义都保存在 Resource.h 中。  但是，你可能需要更改此包含文件名，以便可以在同一个目录下使用多个资源文件。  
  
### 更改资源符号头文件的名称  
  
1.  在[“资源视图”](../windows/resource-view-window.md)中，右键单击 .rc 文件，然后从快捷菜单中选择[“资源包括”](../windows/resource-includes-dialog-box.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**“符号头文件”**框中，为包含文件键入新名称。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)