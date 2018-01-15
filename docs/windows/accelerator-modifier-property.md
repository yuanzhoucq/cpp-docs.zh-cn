---
title: "快捷键 Modifier 属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63d6a4b526fc1f2aeb2a942e682a8c7cc6f9b58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-modifier-property"></a>快捷键 Modifier 属性
以下是用于快捷键对应表中的修饰符属性的合法条目。  
  
|“值”|描述|  
|-----------|-----------------|  
|**无**|用户按下仅将密钥值。 这是最有效地 ASCII/ANSI 与值一起使用 001 026，通过它解释为 ^ A 到 ^ Z (CTRL-A 到 Z CTRL)。|  
|**Alt**|用户必须按 ALT 键前的密钥值。|  
|**Ctrl**|用户必须按 CTRL 键密钥值之前。 与 ASCII 类型无效。|  
|**Shift**|用户必须按下 SHIFT 键密钥值之前。|  
|**Ctrl + Alt**|用户必须按 ctrl 和 ALT 键前的密钥值。 与 ASCII 类型无效。|  
|**Ctrl + Shift**|用户必须按 CTRL 键和 SHIFT 键密钥值之前。 与 ASCII 类型无效。|  
|**Alt + Shift**|用户必须按 ALT 键和 SHIFT 键密钥值之前。 与 ASCII 类型无效。|  
|**Ctrl + Alt + Shift**|密钥值之前，用户必须按下 CTRL、 ALT 和 SHIFT。 与 ASCII 类型无效。|  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [设置快捷键属性](../windows/setting-accelerator-properties.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)