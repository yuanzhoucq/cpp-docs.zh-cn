---
title: "命令行警告 D9025 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9025"
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行警告 D9025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

正在用“option2”重写“option1”  
  
 已指定 *option1* 选项但之后被 *option2* 重写。  *option2* 选项被使用。  
  
 如果两个选项指定的指令相对立或不兼容，则使用命令行最右侧的选项中指定或隐含的指令。  
  
 如果在从开发环境中编译时收到此警告且不能确定冲突选项来自何处，请考虑下列问题：  
  
-   选项既可以在代码中指定，也可以在项目的项目设置中指定。  如果查看编译器的[命令行属性页](../../ide/command-line-property-pages.md)，并在**“所有选项”**字段中看到冲突的选项，则选项是在项目的属性页中设置的；否则，选项是在源代码中设置的。  
  
     如果选项是在项目的属性页中设置的，请查看编译器的预处理器属性页（项目节点在解决方案资源管理器中处于选中状态）。如果在此处看不到设置的选项，请检查各个源代码文件的预处理器属性页设置（在解决方案资源管理器中）以确保它未添加到此处。  
  
     如果选项是在代码中设置的，则既可以在代码中设置，也可以在 windows 头中设置。可以尝试创建一个预处理文件 \([\/P](../../build/reference/p-preprocess-to-a-file.md)\) 并在其中搜索符号。