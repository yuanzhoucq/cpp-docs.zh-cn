---
title: 快捷键 Modifier 属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d99d4656f2835f9adb60f310e429c4ccb97ac7b6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854049"
---
# <a name="accelerator-modifier-property"></a>快捷键 Modifier 属性
以下是用于快捷键对应表中的修饰符属性的合法条目。  
  
|值|描述|  
|-----------|-----------------|  
|**无**|用户按下仅将密钥值。 这是最有效地 ASCII/ANSI 与值一起使用 001 026，通过它解释为 ^ A 到 ^ Z (CTRL-A 到 Z CTRL)。|  
|**Alt**|用户必须按 ALT 键前的密钥值。|  
|**Ctrl**|用户必须按 CTRL 键密钥值之前。 与 ASCII 类型无效。|  
|**Shift**|用户必须按下 SHIFT 键密钥值之前。|  
|**Ctrl + Alt**|用户必须按 ctrl 和 ALT 键前的密钥值。 与 ASCII 类型无效。|  
|**Ctrl + Shift**|用户必须按 CTRL 键和 SHIFT 键密钥值之前。 与 ASCII 类型无效。|  
|**Alt + Shift**|用户必须按 ALT 键和 SHIFT 键密钥值之前。 与 ASCII 类型无效。|  
|**Ctrl + Alt + Shift**|密钥值之前，用户必须按下 CTRL、 ALT 和 SHIFT。 与 ASCII 类型无效。|  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [设置快捷键属性](../windows/setting-accelerator-properties.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)