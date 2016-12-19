---
title: "/NOLOGO（取消显示启动版权标志）（链接器） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.SuppressStartupBanner"
  - "/nologo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOLOGO 链接器选项"
  - "标志, 取消显示启动"
  - "版权信息"
  - "NOLOGO 链接器选项"
  - "-NOLOGO 链接器选项"
  - "取消显示启动版权标志链接器选项"
  - "版本号, 禁止链接器显示"
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOLOGO（取消显示启动版权标志）（链接器）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOLOGO  
```  
  
## 备注  
 \/NOLOGO 选项禁止显示版权消息和版本号。  
  
 该选项还取消命令文件的回显。  有关详细信息，请参见 [LINK 命令文件](../../build/reference/link-command-files.md)。  
  
 默认情况下，该信息由链接器发送到“输出”窗口。  在命令行上，它被发送到标准输出并可以重定向到文件。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  应仅从命令行使用该选项。  
  
### 以编程方式设置此链接器选项  
  
1.  不能以编程方式更改此链接器选项。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)