---
title: "TN020: ID 命名和编号约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.id
dev_langs: C++
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a666c2183276b95a9405400de8acc0117c7134e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020：ID 命名和编号约定
本说明介绍 ID 命名和编号约定 MFC 2.0 使用的资源、 命令、 字符串、 控件和子窗口。  
  
 MFC ID 命名和编号约定旨在满足以下要求：  
  
-   提供在 MFC 库和 MFC 应用程序支持的 Visual c + + 资源编辑器中使用一致的 ID 命名标准。 这便于程序员也要解释的类型和来源的资源从其 id。  
  
-   强调某些类型的 Id 之间的强 1 对 1 关系。  
  
-   符合已广泛使用标准命名 Windows 中的 Id。  
  
-   分区的 ID 编号的空间。 可以通过程序员、 MFC、 Windows 和 Visual c + + 编辑资源分配 ID 号。 适当的分区有助于避免重复的 ID 号。  
  
## <a name="the-id-prefix-naming-convention"></a>ID 前缀的命名约定  
 应用程序可以发生几种类型的 Id。 MFC ID 命名约定定义不同资源类型的不同的前缀。  
  
 MFC 使用的前缀"IDR_"来指示将应用到多个资源类型的资源 ID。 例如，对于给定的框架窗口中，MFC 使用相同的"IDR_"前缀以指示菜单、 快捷键、 字符串和图标资源。 下表显示各种前缀和它们的用法：  
  
|前缀|使用|  
|------------|---------|  
|IDR_|多个资源类型 （主要用于菜单、 加速器和功能区）。|  
|IDD_|对于对话框模板资源 (例如，IDD_DIALOG1)。|  
|IDC_|对于光标资源。|  
|IDI_|对于图标资源。|  
|IDB_|对于位图资源。|  
|IDS_|对于字符串资源。|  
  
 在对话框资源，MFC 遵循这些约定：  
  
|前缀或标签|使用|  
|---------------------|---------|  
|IDOK IDCANCEL|有关标准下压按钮 Id。|  
|IDC_|其他对话框控件。|  
  
 为游标还使用"IDC_"前缀。 此命名冲突通常不问题因为典型的应用程序将具有几个游标和许多对话框控件。  
  
 中的菜单资源，MFC 遵循这些约定：  
  
|前缀|使用|  
|------------|---------|  
|IDM_|不使用 MFC 命令体系结构的菜单项。|  
|ID_|为使用 MFC 命令体系结构的菜单命令。|  
  
 请按照 MFC 命令体系结构的命令必须具有`ON_COMMAND`命令处理程序，并可以`ON_UPDATE_COMMAND_UI`处理程序。 如果这些命令处理程序遵循 MFC 命令体系结构，它们将正常它们是否已绑定到的菜单命令、 工具栏按钮或对话框栏按钮。 相同的"ID_"前缀还用于在程序的消息栏显示的菜单提示字符串。 应用程序中的菜单项的大多数应遵循的 MFC 命令约定。 所有标准命令 Id (例如， `ID_FILE_NEW`) 遵循此约定。  
  
 MFC 还使用"IDP_"作为一种特殊形式的字符串 （而不是"IDS_")。 以"IDP_"前缀的字符串是提示，即，在消息框中使用的字符串。 "IDP_"字符串可以包含"%1"和"%2"作为由程序的字符串的占位符。 "IDP_"字符串通常具有与它们，关联的帮助主题，"IDS_"字符串不能。 始终本地化"IDP_"字符串，并可能不会本地化"IDS_"字符串。  
  
 MFC 库还使用"IDW_"前缀，作为一种特殊形式的控件 （而不是"IDC_") 的 Id。 这些 Id 指派给如视图和拆分条的子窗口的框架类。 MFC 实现 Id 以"AFX_"作为前缀。  
  
## <a name="the-id-numbering-convention"></a>ID 编号约定  
 下表列出的特定类型的 Id 的有效范围。 一些限制是技术实现的限制，而其他则旨在防止你的 Id 与 Windows 预定义的 Id 或 MFC 冲突的默认实现的约定。  
  
 我们强烈建议你定义建议的范围内的所有 Id。 这些范围的下限为 1，因为未使用 0。 我们建议你使用的常见约定，并使用 100 或 101 作为第一个 id。  
  
|前缀|资源类型|有效范围|  
|------------|-------------------|-----------------|  
|IDR_|多个|1 到 0x6FFF|  
|IDD_|对话框模板|1 到 0x6FFF|  
|IDC_，IDI_，IDB_|光标、 图标、 位图|1 到 0x6FFF|  
|IDS_ IDP_|常规字符串|1 到 0x7FFF|  
|ID_|命令|0x8000 到 0xDFFF|  
|IDC_|控件|8 到 0xDFFF|  
  
 这些范围限制的原因是：  
  
-   按照约定，未使用的 ID 值为 0。  
  
-   Windows 实现限制限制真实资源 Id 小于或等于 0x7FFF。  
  
-   MFC 的内部框架保留这些范围：  
  
    -   通过 0x7FFF 0x7000 （请参阅 afxres.h）  
  
    -   通过 0xEFFF 0xE000 （请参阅 afxres.h）  
  
    -   16000 通过 18000 （请参阅 afxribbonres.h）  
  
     这些范围可能会在将来更改 MFC 的实现。  
  
-   多个 Windows 系统命令使用 0xF000 到 0xFFFF 的范围。  
  
-   标准控件，如 IDOK 和 IDCANCEL 保留的 1 到 7 的控件 Id。  
  
-   0x8000 到字符串的 0xFFFF 范围留待菜单会提示你输入命令。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

