---
title: "创建提供程序 | Microsoft Docs"
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
  - "OLE DB 提供程序, 创建"
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

#### 用“ATL OLE DB 提供程序向导”创建 OLE DB 提供程序  
  
1.  右击该项目。  
  
2.  在快捷菜单上，单击“添加”，然后单击“添加类”。  
  
3.  在**“添加类”**对话框中，选择**“ATL OLE DB 提供程序”**图标，然后单击**“打开”**。  
  
4.  在“ATL OLE DB 提供程序向导”中，在**“简称”**框中输入提供程序的简称。  以下主题使用简称“MyProvider”，但您可以使用其他名称。  其他名称框根据您输入的名称填充。  
  
5.  如果需要，编辑其他名称框。  除了对象名和文件名，还可以编辑以下内容：  
  
    -   “CoClass”：COM 用于创建提供程序的名称。  
  
    -   **“ProgID”**：编程标识符，可用来代替 GUID 的文本字符串。  
  
    -   **“版本”**：与 ProgID 和 coclass 一起使用以生成版本相关的编程 ID。  
  
6.  单击**“完成”**。  
  
## 请参阅  
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)