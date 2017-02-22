---
title: "具有块范围的名称中的链接 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "块范围 [C++]"
  - "外部链接, 范围链接规则"
  - "链接 [C++], 范围链接规则"
  - "名称 [C++], 范围链接规则"
  - "范围 [C++], 链接规则"
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 具有块范围的名称中的链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列链接规则适用于具有块范围的名称（本地名称）：  
  
-   声明为 `extern` 的名称具有外部链接，除非它们以前声明为 **static**。  
  
-   没有块范围的所有其他名称都没有链接。  
  
## 请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)