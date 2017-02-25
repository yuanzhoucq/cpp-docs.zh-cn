---
title: "Symbol Name Restrictions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.restrictions.name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
  - "restrictions, symbol names"
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Symbol Name Restrictions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对符号名的限制如下所示：  
  
-   所有[符号](../mfc/symbols-resource-identifiers.md)在应用程序的范围内都必须唯一。  这样可防止头文件中出现冲突的符号定义。  
  
-   符号名的有效字符包括 A\-Z、a\-z、0\-9 和下划线 \(\_\)。  
  
-   符号名不能以数字开头，仅限于 247 个字符。  
  
-   符号名不能包含空格。  
  
-   符号名不区分大小写，但是第一个符号定义的大小写会保留。  定义符号的头文件由资源编译器\/编辑器和 C\+\+ 程序用于引用资源文件中定义的资源。  对于只有大小写不同的两个符号名，C\+\+ 程序会看到两个单独的符号，而资源编译器\/编辑器将这两个名称视为引用单个符号。  
  
    > [!NOTE]
    >  如果不遵循下面概述的标准符号名方案（ID\*\_\[关键字\]），并且符号名恰好与资源脚本编译器已知的关键字相同，则尝试生成资源脚本文件会导致看似难以进行诊断的随机错误生成。  若要防止出现此情况，请遵循标准命名方案。  
  
 符号名具有描述性前缀，可指示它们所表示的资源或对象的类型。  这些描述性前缀以文本组合 ID 开头。  Microsoft 基础类库 \(MFC\) 使用下表中所示的符号命名约定。  
  
|类别|前缀|使用|  
|--------|--------|--------|  
|资源|IDR\_ IDD\_ IDC\_ IDI\_ IDB\_|加速器或菜单（以及关联或自定义资源） 对话框 光标 图标 位图|  
|菜单项|ID\_|Menu item|  
|命令|ID\_|命令|  
|控件和子窗口|IDC\_|控件|  
|字符串|IDS\_|字符串表中的字符串|  
|MFC|AFX\_|为预定义 MFC 符号保留|  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源以及将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Changing a Symbol or Symbol Name \(ID\)](../windows/changing-a-symbol-or-symbol-name-id.md)   
 [Symbol Value Restrictions](../windows/symbol-value-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)