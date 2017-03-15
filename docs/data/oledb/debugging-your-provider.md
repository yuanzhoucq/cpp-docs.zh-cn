---
title: "调试提供程序 | Microsoft Docs"
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
  - "调试 [C++], 提供程序"
  - "OLE DB 提供程序, 调试"
  - "Visual C++ 调试器"
  - "Visual C++ 调试器, 调试提供程序"
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 调试提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有两种方法调试提供程序：  
  
-   因为提供程序是在进程中创建的，可以用 OLE DB 使用者模板创建一些使用者代码，并按正常方式进入并单步执行提供程序。  
  
-   可以使用 Visual C\+\+ 附带的 ITEST 实用工具。  
  
### 使用 ITEST 实用工具  
  
1.  打开提供程序项目。  
  
2.  在**“项目”**菜单上单击**“设置”**。  
  
3.  在**“属性页”**对话框中单击**“调试”**选项卡。  
  
4.  在“调试会话的可执行文件”框中，选择“ITEST”应用程序。  
  
5.  设置断点并像通常那样调试。  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)