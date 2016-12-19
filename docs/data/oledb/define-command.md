---
title: "DEFINE_COMMAND | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND 宏"
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DEFINE_COMMAND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定要用于创建该行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md) 类中的命令。  接受与指定的应用程序类型的某些字符串类型 \(ANSI 或 Unicode。\)  
  
> [!NOTE]
>  建议您改用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) 而不是 `DEFINE_COMMAND`。  
  
## 语法  
  
```  
  
DEFINE_COMMAND(  
x  
,   
szCommand  
 )  
  
```  
  
#### 参数  
 *x*  
 \[in\] 用户记录（命令）类的名称。  
  
 `szCommand`  
 \[in\] 将用于为行集合，并使用 [CCommand](../../data/oledb/ccommand-class.md)中的命令字符串。  
  
## 备注  
 您所指定的命令字符串将使用为默认，如果您在 [CCommand::Open](../../data/oledb/ccommand-open.md) 方法不指定命令文本。  
  
 此宏接受 ANSI 字符串，如果生成应用程序，为 ANSI 或 Unicode 字符串，则应用程序生成为 Unicode。  建议您改用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) 而不是 `DEFINE_COMMAND`，因为前面接受，Unicode 字符串，而 ANSI 或 Unicode，应用程序类型。  
  
## 示例  
 参见 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)