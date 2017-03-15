---
title: "项目生成错误 PRJ0025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0025"
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 项目生成错误 PRJ0025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

批处理文件“file”包含未能翻译成用户 ANSI 代码页的 Unicode 内容。  
  
 ***文件的 UNICODE 内容***  
  
 项目系统在自定义生成规则或生成事件中发现了不能正确翻译成用户的当前 ANSI 代码页的 Unicode 内容。  
  
 该错误的解决方法是更新生成规则或生成事件的内容以使用 ANSI，或在计算机上安装代码页并将其设置为系统的默认代码页。  
  
 有关自定义生成步骤和生成事件的更多信息，请参见[了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)。