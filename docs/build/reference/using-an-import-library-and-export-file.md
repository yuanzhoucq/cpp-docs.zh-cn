---
title: "使用导入库和导出文件 | Microsoft Docs"
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
  - "循环导出"
  - "导出文件"
  - "导入库, using"
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用导入库和导出文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当某程序（可执行文件或 DLL）导出到的另一个程序同时也是它从中导入的程序时，或者两个以上的程序相互导出和导入时，链接这些程序的命令必须提供循环导出。  
  
 在没有循环导出的情况中，当链接的程序使用另一个程序的导出时，必须指定导出程序的导入库。  当链接到导出程序时创建那个导出程序的导入库。  因此，必须在导入程序之前链接导出程序。  例如，如果 TWO.dll 从 ONE.dll 导入，则必须首先链接 ONE.dll 并获取导入库 ONE.lib。  然后，在链接 TWO.dll 时指定 ONE.lib。  链接器在创建 TWO.dll 时还会创建其导入库 TWO.lib。  当链接从 TWO.dll 导入的程序时使用 TWO.lib。  
  
 但是，在循环导出的情况中，不可能使用其他程序的导入库来链接所有相互依赖的程序。  在刚才讨论的示例中，如果 TWO.dll 也导出到 ONE.dll，则 TWO.dll 的导入库在链接 ONE.dll 时尚不存在。  当存在循环导出时，必须使用 LIB 为其中某个程序创建导入库和导出文件。  
  
 首先，选择要对其运行 LIB 的其中某个程序。  在 LIB 命令中，列出该程序的所有对象和库并指定 \/DEF。  如果程序使用 .def 文件或 \/EXPORT 规范，则也要指定这些内容。  
  
 为该程序创建导入库 \(.lib\) 和导出文件 \(.exp\) 后，在链接其他程序时使用该导入库。  LINK 为生成的每个导出程序创建一个导入库。  例如，如果对 ONE.dll 的对象和导出运行 LIB，则将创建 ONE.lib 和 ONE.exp。  现在，在链接 TWO.dll 时可使用 ONE.lib；此步骤还创建导入库 TWO.lib。  
  
 最后，链接最初使用的那个程序。  在 LINK 命令中，指定该程序的对象和库、LIB 为该程序创建的 .exp 文件以及该程序使用的导出的导入库。  为了继续此示例，ONE.dll 的 LINK 命令中除了包含导入到 ONE.dll 中的对象和库外，还包含 ONE.exp 和 TWO.lib。  不要在 LINK 命令中指定 .def 文件或 \/EXPORT 规范；由于在 .exp 文件中包含了导出定义，因此并不需要这些内容。  当使用 .exp 文件进行链接时，LINK 并不创建导入库，因为它假定在创建 .exp 文件时已经创建了一个。  
  
## 请参阅  
 [使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)