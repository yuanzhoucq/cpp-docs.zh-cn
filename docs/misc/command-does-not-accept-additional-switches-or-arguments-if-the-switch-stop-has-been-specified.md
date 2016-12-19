---
title: "Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00CD"
  - "vs.message.VS_E_NOTVALIDWITHSTOP"
ms.assetid: 1dea2450-034e-4a7f-b959-2060811329b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified.
该错误通常发生在与“在文件中查找”或“在文件中替换”命令的其他开关一起输入了 `/stop` 开关时。  
  
### 更正此错误  
  
1.  若要停止当前“在文件中查找”操作，输入：  
  
    ```  
    Edit.FindinFiles /stop.  
    ```  
  
2.  若要停止当前“在文件中替换”操作，输入：  
  
    ```  
    Edit.ReplaceinFiles /stop  
    ```  
  
3.  若要开始新的“在文件中查找”或“在文件中替换”操作，重新输入命令，省略 `/stop`。  
  
## 请参阅  
 [“在文件中替换”命令](../Topic/Replace%20In%20Files%20Command.md)   
 [“在文件中查找”命令](../Topic/Find%20in%20Files%20Command.md)   
 [Visual Studio 命令](../Topic/Visual%20Studio%20Commands.md)