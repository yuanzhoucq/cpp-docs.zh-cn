---
title: "格式化输出的自定义生成步骤或生成事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53720e93c7d45f1eaeb0e62749194720373bee1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>设置自定义生成步骤或生成事件输出的格式
如果自定义生成步骤或生成事件的输出的格式正确，用户将获得以下优势：  
  
-   警告和错误中将计入**输出**窗口。  
  
-   输出显示在**任务列表**窗口。  
  
-   单击中的输出**输出**窗口显示的相应主题。  
  
-   在启用 F1 操作**任务列表**窗口或**输出**窗口。  
  
 输出的格式应为：  
  
 {*filename* (*行 #* [，*列 #*]) &#124;*toolname*} **:**  
  
 [*任何文本*] {**错误**&#124;**警告**}*代码 # # #***:***可本地化的字符串*  
  
 [*任何文本*]  
  
 其中：  
  
-   { &#124;*b*} 是其中任何一个选择或*b*。  
  
-   [`ccc`] 是可选的字符串或参数。  
  
 例如:  
  
 C:\\*sourcefile.cpp*(134): 错误 C2143： 语法错误： 缺少; 之前}  
  
 链接： 致命错误 LNK1104： 无法打开文件*somelib.lib*  
  
## <a name="see-also"></a>请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)