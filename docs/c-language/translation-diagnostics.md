---
title: "转换：诊断 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 525f8c235a4c2500b09ac37a050d4b57fadc8fb9
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

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
