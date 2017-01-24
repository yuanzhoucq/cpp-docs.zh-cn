---
title: "CRecentFileList Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecentFileList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecentFileList class"
  - "文件 [C++], most recently used"
  - "MRU 文件"
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRecentFileList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持最近使用的\(MRU\)文件的控件的列表。  
  
## 语法  
  
```  
class CRecentFileList  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRecentFileList::CRecentFileList](../Topic/CRecentFileList::CRecentFileList.md)|构造 `CRecentFileList` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRecentFileList::Add](../Topic/CRecentFileList::Add.md)|将文件添加到MRU文件列表。|  
|[CRecentFileList::GetDisplayName](../Topic/CRecentFileList::GetDisplayName.md)|为MRU文件名的菜单显示提供的显示名称。|  
|[CRecentFileList::GetSize](../Topic/CRecentFileList::GetSize.md)|检索文件数。MRU文件的列表。|  
|[CRecentFileList::ReadList](../Topic/CRecentFileList::ReadList.md)|读取MRU文件从注册表或.INI文件列表。|  
|[CRecentFileList::Remove](../Topic/CRecentFileList::Remove.md)|从MRU文件删除文件列表。|  
|[CRecentFileList::UpdateMenu](../Topic/CRecentFileList::UpdateMenu.md)|更新MRU文件的菜单显示列表。|  
|[CRecentFileList::WriteList](../Topic/CRecentFileList::WriteList.md)|MRU文件从注册表或.INI文件列表中编写。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CRecentFileList::operator](../Topic/CRecentFileList::operator.md)|返回 `CString` 对象在特定位置。|  
  
## 备注  
 文件中添加或删除从MRU文件列表中，文件列表可以读取或写入注册表或文件，.INI，并显示MRU文件的菜单列出了可以更新。  
  
 有关MRU菜单项的更多信息，请参见  
  
-   知识库文章Q243751:HOWTO:添加MRU菜单项的命令处理程序在MFC应用程序  
  
## 继承层次结构  
 `CRecentFileList`  
  
## 要求  
 **Header:** afxadv.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)