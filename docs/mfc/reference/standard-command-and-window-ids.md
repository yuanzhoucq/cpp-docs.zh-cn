---
title: "标准命令和窗口 ID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "标准命令和 Window ID"
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 标准命令和窗口 ID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类库定义了 Afxres.h 的许多和 Windows 标准命令 ID。  这些 ID 在资源编辑器和"属性"窗口中最常使用的映射到消息处理程序函数。  所有标准命令具有 **ID\_** 前缀。  例如，在菜单编辑器，使用时，您通常将文件打开菜单项为 `ID_FILE_OPEN` . 标准命令 ID  
  
 对于大多数标准命令，您的应用程序代码不需要引用命令 ID，因为框架通过它在主框架类 \(`CWinThread`、`CWinApp`、`CView`，**CDocument**的消息映射处理命令，等等\)。  
  
 除了标准命令 ID 之外，具有 **AFX\_ID**前缀的许多其他标准 ID 被定义。  这些 ID 包含标准窗口 ID \( **AFX\_IDW\_**\)，前缀的字符串 ID\) 前缀 \( **AFX\_IDS\_**\) 和若干其他类型。  
  
 **AFX\_ID** 以前缀开头，程序员，但很少使用的 ID 可能需要参考还指 **AFX\_ID**的 . 的这些 ID，并重写框架时函数。  
  
 此 ID 引用没有单个文档。  可以查找有关它们的详细信息在方法声明、[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)[21](../../mfc/tn021-command-and-message-routing.md)和 [22](../../mfc/tn022-standard-commands-implementation.md)。  
  
> [!NOTE]
>  头文件 Afxres.h 在 Afxwin.h 间接包含。  您必须显式包括在应用程序的资源脚本 \(.rc\) 文件中以下语句：  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/CPP/standard-command-and-window-ids_1.h)]  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)