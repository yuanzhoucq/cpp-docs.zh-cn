---
title: "内部链接 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "内部链接"
  - "链接 [C++], 内部"
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 内部链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果对象或函数的文件范围标识符声明包含 *storage\-class\-specifier* **static**，则该标识符具有内部链接。  否则，该标识符具有外部链接。  有关 *storage\-class\-specifier* 非终止符的讨论，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 在一个翻译单元内，带内部链接的标识符的每个实例均表示相同的标识符或函数。  内部链接的标识符对于翻译单元是唯一的。  
  
## 请参阅  
 [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)