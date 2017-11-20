---
title: "转换：诊断 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb7f826be88ebec640a6f3b40b38478eea91ed36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="translation-diagnostics"></a>转换：诊断
**ANSI 2.1.1.3** 如何标识诊断  
  
 Microsoft C 生成以下形式的错误消息：  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 其中，filename 是出现错误的源文件的名称；line-number 是编译器在其中检测到错误的行号；`diagnostic` 是“错误”或“警告”；`number` 是标识错误或警告的唯一的四位数（前面带有 C，如语法中所注明的）；`message` 是解释性消息。  
  
## <a name="see-also"></a>另请参阅  
 [实现定义的行为](../c-language/implementation-defined-behavior.md)