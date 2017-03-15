---
title: "DEFINE_COMMAND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND_EX 宏"
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DEFINE_COMMAND_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定要用于创建该行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md) 类中的命令。  支持 Unicode 和 ANSI 应用程序。  
  
## 语法  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
```  
  
#### 参数  
 *x*  
 \[in\] 用户记录 \(\) 命令类的名称。  
  
 `wszCommand`  
 \[in\] 将用于为行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md)中的命令字符串。  
  
## 备注  
 您所指定的命令字符串将使用为默认，如果您在 [CCommand::Open](../../data/oledb/ccommand-open.md) 方法不指定命令文本。  
  
 无论应用程序类型，此宏接受，Unicode 字符串。  因为它支持 Unicode 以及 ANSI 应用程序，则此宏优于 [DEFINE\_COMMAND](../../data/oledb/define-command.md)。  
  
## 示例  
 参见 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)