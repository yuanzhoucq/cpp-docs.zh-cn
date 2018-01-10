---
title: "模块定义语句的规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .def
dev_langs: C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40eb4875b195871aff8d274667e005d63424a110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rules-for-module-definition-statements"></a>模块定义语句的规则
下面的语法规则应用于.def 文件中的所有语句。 与每个语句描述了适用于特定语句其他规则。  
  
-   语句、 属性关键字和用户指定的标识符区分大小写。  
  
-   长文件名包含空格或分号 （;） 的名称必须用引号引起来 （"）。  
  
-   将语句关键字单独从其自变量，将从每个其他语句分隔使用一个或多个空格、 制表符或换行字符。 冒号 （:） 或括零或多个空格、 制表符或换行字符在等号 （=），它指定自变量。  
  
-   A**名称**或**库**语句，如果使用，必须所有其他语句之前。  
  
-   **部分**和**导出**语句可以多次出现在.def 文件。 每个语句都可以采用多个规范，后者必须按一个或多个空格、 制表符或换行符分隔。 语句关键字必须出现一次在第一种规范之前，并且可以在每个附加规范之前重复。  
  
-   很多语句具有等效的链接命令行选项。 请参阅有关其他详细信息的相应链接选项的说明。  
  
-   .Def 文件中的注释来指定分号 （;） 在每个注释行的开头。 注释不能使用一个语句，共享一条线路，但它可以出现在多行语句中的规范之间。 (**部分**和**导出**多行语句。)  
  
-   数值参数均为指定以 10 为基数或十六进制。  
  
-   如果字符串自变量与匹配[保留字](../../build/reference/reserved-words.md)，它必须括在双引号 （"）。  
  
## <a name="see-also"></a>请参阅  
 [模块定义 (.Def) 文件](../../build/reference/module-definition-dot-def-files.md)  