---
title: "MFC 数据库文档 | Microsoft Docs"
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
  - "DAO [C++], MFC"
  - "数据库 [C++], MFC"
  - "MFC [C++], 数据库应用程序"
  - "ODBC [C++], MFC"
ms.assetid: bb120282-cd0d-4bf4-a27c-93b3501fb3a0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC 数据库文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DAO 和 ODBC 类的 MFC 文档包含下表中列出的组件：  
  
### MFC 数据库文档  
  
|有关文档|请参见|  
|----------|---------|  
|DAO 和 ODBC 的类|“MFC 参考”中的类名|  
|DAO 和 ODBC 的全局函数和宏|“MFC 参考”中的函数名或宏名|  
|使用 MFC ODBC 类编程|[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)|  
|DAO 和 ODBC 的技术说明|[MFC 技术说明](../mfc/technical-notes-by-category.md)|  
  
##  <a name="_core_mfc_documentation_and_dao_documentation"></a> MFC 文档和 DAO 文档  
 在 MFC DAO 类的 MFC 文档中，随处可见对 DAO SDK 文档（包含在联机文档中）中的主题的引用。  因为 MFC 封装或（包装）DAO，所以 MFC 文档：  
  
-   着重介绍 MFC 以及它与基础 DAO 实现有哪些不同。  
  
-   引导用户至 DAO SDK 帮助主题，以获取基础详细信息。  这些交叉引用的措辞都是“DAO 帮助中的 X 主题”。  
  
-   指出 MFC 和 DAO 在工作方式上的不同之处。  MFC 并不包装所有 DAO。  例如，MFC 不为对象提供 DAO 安全功能。  
  
> [!NOTE]
>  DAO SDK 帮助是一个单独的帮助文件。  在本版本的 Visual C\+\+ 中，没有从本文档到 DAO 帮助的超文本链接。  
  
> [!NOTE]
>  浏览 DAO SDK 帮助中的主题时，您也许需要做一些翻译。  DAO SDK 主文档中的示例使用 Basic 编程语言而非 C\+\+ 编写而成。（而 DAO SDK 提供的 C\+\+ 示例集并未使用 MFC。）  
  
##  <a name="_core_mfc_documentation_and_odbc_documentation"></a> MFC 文档和 ODBC 文档  
 MFC ODBC 类的 MFC 文档具有不同的组织方式。  MFC ODBC 类提供依赖 ODBC 而非 ODBC API 包装的高级抽象。  所以，相比 MFC 和 DAO 文档组来说，这两组文档之间的联结较少。  ODBC 文档使用比 Basic 更接近 C\+\+ 的 C 语言。  
  
## 请参阅  
 [MFC 数据库类（ODBC 和 DAO）](../data/mfc-database-classes-odbc-and-dao.md)   
 [ODBC 基础](../data/odbc/odbc-basics.md)