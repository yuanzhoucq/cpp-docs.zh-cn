---
title: "快捷键 Modifier 属性 | Microsoft Docs"
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
  - "Modifier 属性"
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 快捷键 Modifier 属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面是快捷键对应表中 Modifier 属性的合法项。  
  
|值|说明|  
|-------|--------|  
|**无**|用户仅按 Key 值。  这非常适合于与从 001 到 026 的 ASCII\/ANSI 值一起使用，这些值被解释为从 ^A 到 ^Z，即从 Ctrl\-A 到 Ctrl\-Z。|  
|**Alt**|用户在按 Key 值前必须按 Alt 键。|  
|**Ctrl**|用户在按 Key 值前必须按 Ctrl 键。  对 ASCII 类型无效。|  
|**Shift**|用户在按 Key 值前必须按 Shift 键。|  
|**Ctrl\+Alt**|用户在按 Key 值前必须按 Ctrl 键和 Alt 键。  对 ASCII 类型无效。|  
|**Ctrl\+Shift**|用户在按 Key 值前必须按 Ctrl 键和 Shift 键。  对 ASCII 类型无效。|  
|**Alt\+Shift**|用户在按 Key 值前必须按 Alt 键和 Shift 键。  对 ASCII 类型无效。|  
|**Ctrl\+Alt\+Shift**|用户在按 Key 值前必须按 Ctrl、Alt 和 Shift 键。  对 ASCII 类型无效。|  
  
## 要求  
 Win32  
  
## 请参阅  
 [Setting Accelerator Properties](../windows/setting-accelerator-properties.md)   
 [Accelerator Editor](../mfc/accelerator-editor.md)