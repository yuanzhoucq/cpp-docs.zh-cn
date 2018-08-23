---
title: 设置自定义生成步骤或生成事件输出的格式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7da71e6391d2d3223b47ba528686d2fec003ab3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321345"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>设置自定义生成步骤或生成事件输出的格式
如果自定义生成步骤或生成事件的输出格式正确，则用户将获得以下好处：  
  
-   警告和错误将在“输出”窗口中计数。  
  
-   在“任务列表”窗口中显示输出。  
  
-   单击“输出”窗口中的输出，显示相应主题。  
  
-   可在“任务列表”窗口或“输出”窗口中启用 F1 操作。  
  
 输出格式应为：  
  
 {filename (line# [, column#]) &#124; toolname} :  
  
 [any text] {error &#124; warning} code####:localizable string**  
  
 [ any text ]  
  
 其中：  
  
-   {a &#124; b} 表示在 a 或 b 中任选一个。  
  
-   [`ccc`] 为可选的字符串或参数。  
  
 例如:  
  
 C:\\sourcefile.cpp(134) : 错误 C2143: 语法错误 : "}" 前缺少 ";"  
  
 LINK : 灾难性错误 LNK1104: 无法打开文件 "somelib.lib"  
  
## <a name="see-also"></a>请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)