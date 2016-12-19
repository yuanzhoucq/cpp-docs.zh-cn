---
title: "初始值设定项列表 | Microsoft Docs"
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
  - "初始值设定项列表"
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始值设定项列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

现在会在调用基类构造函数之前调用构造函数中的初始值设定项列表。  
  
## 备注  
 在 Visual C\+\+ 2005 之前，使用 C\+\+ 托管扩展进行编译时会在调用初始值设定项列表之前调用基类构造函数。  现在使用 **\/clr** 进行编译时则会先调用初始值设定项列表。  
  
## 请参阅  
 [常规语言更改](../dotnet/general-language-changes-cpp-cli.md)