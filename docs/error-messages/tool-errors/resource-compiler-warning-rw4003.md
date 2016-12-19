---
title: "资源编译器警告 RW4003 | Microsoft Docs"
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
  - "RW4003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW4003"
ms.assetid: e9c289f2-c065-4f26-bc24-991953742abc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器警告 RW4003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在没有 VIRTKEY 的情况下使用了 Shift 或 Ctrl  
  
 在快捷键表资源中，Shift 或 Ctrl 要求 VIRTKEY。  因为 Shift 或 Ctrl 被指示为 VIRTKEY 类型快捷键中的标志位，它们无法离开 VIRTKEY 而独立存在。