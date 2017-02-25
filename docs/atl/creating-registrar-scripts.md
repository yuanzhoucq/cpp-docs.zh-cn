---
title: "Creating Registrar Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 注册表"
  - "registrar scripts [ATL]"
  - "脚本编写, registry scripting"
  - "脚本, 创建"
  - "脚本, Registrar scripts"
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating Registrar Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注册器脚本提供数据驱动的，而不是API开始，到系统注册表的访问。  因为它只接受在脚本中用行将该密钥添加到注册表，数据驱动的访问是通常更为高效。  
  
 [ATL控件向导](../atl/reference/atl-control-wizard.md) 自动为您生成COM服务器的controllers脚本。  可以找到在.rgs文件的此脚本与对象关联的。  
  
 ATL控制器的脚本引擎处理您的管理员脚本在运行时。  在服务器上安装过程中，ATL自动调用脚本引擎。  
  
 本文包含以下主题与管理员脚本有关:  
  
-   [了解的Backus Nauer窗体\(BNF\)语法](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [了解分析树](../atl/understanding-parse-trees.md)  
  
-   [注册表脚本示例](../atl/registry-scripting-examples.md)  
  
-   [使用可替换参数\(控制器的预处理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [调用脚本](../atl/invoking-scripts.md)  
  
## 请参阅  
 [注册表组件（注册器）](../atl/atl-registry-component-registrar.md)