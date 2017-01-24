---
title: "CString Semantics | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "赋值语句, assigning CString objects"
  - "CString objects, assignment semantics"
  - "semantics in Cstring"
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CString Semantics
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

即使 [CString](../atl-mfc-shared/reference/cstringt-class.md) 对象是可根据的动态对象，它们象内置基元类型和简单的选件类。  每 `CString` 对象表示单个值。  应值`CString` 对象作为实际字符串而不是指向字符串。  
  
 可以将一 **CString** 对象到另一个。  但是，那么，当您修改两 `CString` 对象之一时，另一 `CString` 对象不会修改，如显示按以下示例:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/CPP/cstring-semantics_1.cpp)]  
  
 在此示例中的说明两 `CString` 对象视为“相等”，因为它们表示同一字符字符串。  `CString` 选件类重载相等运算符\(`==`\)比较依据值的两 `CString` 对象\(或目录\)而不是它们的标识\(地址）。  
  
## 请参阅  
 [字符串](../atl-mfc-shared/strings-atl-mfc.md)