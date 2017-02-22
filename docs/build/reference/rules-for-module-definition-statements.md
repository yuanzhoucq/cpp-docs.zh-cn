---
title: "模块定义语句的规则 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "模块定义文件"
  - "模块定义文件, 语句语法"
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 模块定义语句的规则
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列语法规则适用于 .def 文件中的所有语句。  其他适用于特定语句的规则与各语句一起加以说明。  
  
-   语句、特性关键字和用户指定的标识符区分大小写。  
  
-   包含空格或分号 \(;\) 的长文件名必须用引号 \("\) 引起。  
  
-   使用一个或多个空格、制表符或换行符，将语句关键字同其参数分开和将各语句分开。  指定参数的冒号 \(:\) 或等号 \(\=\) 两旁有零个或多个空格、制表符或换行符。  
  
-   如果使用 **NAME** 或 **LIBRARY** 语句，则这些语句必须位于所有其他语句之前。  
  
-   在 .def 文件中，**SECTIONS** 和 **EXPORTS** 语句可以出现多次。  每个语句都可以采用多个规范，各规范间必须用一个或多个空格、制表符或换行符分开。  语句关键字必须在第一个规范的前面出现一次，并且可以在每个附加规范的前面重复。  
  
-   许多语句都具有等效的 LINK 命令行选项。  有关其他详细信息，请参见相应的 LINK 选项说明。  
  
-   .def 文件中的注释由每个注释行开始处的分号 \(;\) 指定。  注释不能与语句共享一行，但可以在多行语句的规范间出现。（**SECTIONS** 和 **EXPORTS** 为多行语句。）  
  
-   以十进制或十六进制为基础指定数值参数。  
  
-   如果字符串参数与[保留字](../../build/reference/reserved-words.md)匹配，则必须用双引号 \("\) 将字符串参数引起。  
  
## 请参阅  
 [模块定义 \(.Def\) 文件](../../build/reference/module-definition-dot-def-files.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/zh-cn/56a3bb8f-0181-4989-bab4-a07ba950ab08)