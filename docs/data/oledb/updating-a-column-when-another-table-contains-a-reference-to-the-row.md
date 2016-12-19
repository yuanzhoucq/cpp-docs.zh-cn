---
title: "当另一个表包含行引用时更新列 | Microsoft Docs"
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
  - "行集合, 列更新"
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 当另一个表包含行引用时更新列
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

某些提供程序可以检测到行中发生更改的列，但许多提供程序却做不到。  因此，当存在对尝试更新的行的引用时，更新列可能导致错误。  若要解决此问题，请另外创建一个仅包含要更改的列的访问器。  将此访问器的编号传递给 `SetData`。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)