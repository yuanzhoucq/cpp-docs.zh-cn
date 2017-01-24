---
title: "编译器警告（等级 1）C4656 | Microsoft Docs"
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
  - "C4656"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4656"
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4656
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 从上次生成以来，数据类型是新的或已更改，或在其他地方以不同的方式声明  
  
 您添加或更改了数据类型，该数据类型对于上次成功生成的源代码而言是一种新类型。  “编辑并继续”不支持对现有数据类型的更改。  
  
 此警告后面将始终带有[错误 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。  有关进一步的信息，请参见[受支持的代码更改](../Topic/Supported%20Code%20Changes%20\(C++\).md)。  
  
### 若要移除该警告而不结束当前的调试会话  
  
1.  将数据类型更改回出错前的状态。  
  
2.  从“调试”菜单上选择“应用代码更改”。  
  
### 若要移除该错误而不更改源代码  
  
1.  从**“调试”**菜单中选择**“停止调试”**。  
  
2.  从**“生成”**菜单中选择**“生成”**。