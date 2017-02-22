---
title: "register 存储类说明符 | Microsoft Docs"
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
  - "注册存储类"
  - "注册变量"
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# register 存储类说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 Microsoft C\/C\+\+ 编译器不会按照用户请求来使用寄存器变量。  但是，出于可移植性考虑，编译器将遵循所有与 **register** 关键字关联的其他语义。  例如，您无法将一元 address\-of 运算符 \(**&**\) 应用于寄存器对象，也无法在数组上使用 **register** 关键字。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内部级别声明的存储类说明符](../c-language/storage-class-specifiers-for-internal-level-declarations.md)