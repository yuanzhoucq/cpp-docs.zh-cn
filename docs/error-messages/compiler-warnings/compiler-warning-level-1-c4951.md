---
title: "编译器警告（等级 1）C4951 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4951"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4951"
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4951
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

收集配置文件数据后已编辑过“函数”，没有使用函数配置文件数据  
  
 在输入模块中已将函数编辑为 [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此配置文件数据现在无效。 在 **\/ltcg: pginstrument** 后已重新编译输入模块并且有一个函数（***函数***），使用的控制流不是在执行 **\/ltcg: pginstrument** 操作时模块中的控制流。  
  
 此警告为信息性。 若要解决此警告，请运行 **\/LTCG:PGINSTRUMENT**，重做所有测试，并运行 **\/LTCG:PGOPTIMIZE**。  
  
 如果已使用 **\/LTCG:PGOPTIMIZE**，此警告将替换为一个错误。