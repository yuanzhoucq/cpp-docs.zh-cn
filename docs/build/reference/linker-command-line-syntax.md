---
title: "链接器命令行语法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "LINK 工具 [C++], 命令行语法"
  - "链接器 [C++], 语法"
  - "链接器命令行 [C++]"
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器命令行语法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

要运行 LINK.EXE，可使用下列命令语法：  
  
```  
LINK arguments  
```  
  
 `arguments` 包括选项和文件名，可按任意顺序指定它。  首先处理选项，然后是文件。  使用一个或多个空格或制表符分隔参数。  
  
> [!NOTE]
>  您只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符处启动此工具。  而不能从系统命令提示符或文件资源管理器中启动此工具。  
  
 在命令行上，选项由选项说明符（一个短划线 \(\-\) 或一个正斜杠 \(\/\)）后接该选项的名称组成。  选项名不能缩写。  某些选项带参数，参数在冒号 \(:\) 后指定。  在选项规范中不允许有空格或制表符，但在 \/COMMENT 选项中用引号括起来的字符串中除外。  用十进制或 C 语言表示法指定数值参数。  选项名及其关键字或文件名参数不区分大小写，但用作参数的标识符区分大小写。  
  
 要将文件传递给链接器，在命令行上 LINK 命令之后指定文件名。  可以使用文件名指定绝对路径或相对路径，并且可在文件名中使用通配符。  如果忽略了点 \(.\) 和文件扩展名，则 LINK 将在查找文件时假定扩展名为 .obj。  LINK 不根据文件扩展名是什么或是否存在扩展名来判断文件的内容；它通过检查文件来确定文件类型，并据此处理它。  
  
 link.exe 返回零表示成功（无错误）。否则，链接器将返回使链接停止的错误编号。例如，如果生成 LNK1104，链接器，链接器返回 1104。相应地，在返回错误的最低的错误号由链接器为 1000。返回值具有 128 操作系统或 .config 文件表示配置问题；加载程序未加载或 link.exe c2.dll。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)