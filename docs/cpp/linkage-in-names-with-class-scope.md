---
title: "具有类范围的名称中的链接 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类名 [C++], 链接"
  - "类范围 [C++], 名称中的链接"
  - "类 [C++], 名称"
  - "类 [C++], 范围"
  - "外部链接, 范围链接规则"
  - "链接 [C++], 范围链接规则"
  - "名称 [C++], 范围链接规则"
  - "范围 [C++], 类名"
  - "范围 [C++], 链接规则"
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 具有类范围的名称中的链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列链接规则将应用于具有类范围的名称：  
  
-   静态类成员具有外部链接。  
  
-   类成员函数具有外部链接。  
  
-   枚举器和 `typedef` 名称没有链接。  
  
 **Microsoft 专用**  
  
-   声明为 `friend` 的函数必须具有外部链接。  将静态函数声明为 `friend` 将生成错误。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)