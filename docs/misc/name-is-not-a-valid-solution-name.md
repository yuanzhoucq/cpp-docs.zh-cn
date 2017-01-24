---
title: "&lt;name&gt; is not a valid solution name. | Microsoft Docs"
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
  - "vs.message.VS_E_INVALIDSOLUTIONNAME"
  - "vs.message.0x800A00D3"
ms.assetid: 79b7870d-16bd-4527-8ce6-ffb015e7e330
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid solution name.
该错误通常发生在在**命令**窗口或**查找\/命令**框输入了命令 `File.NewProject`，而其参数 \/sln:*solutionname* 的值格式不正确时。  
  
### 更正此错误  
  
1.  重新键入命令语法并省略可选参数 \/sln:*solutionname*。  将自动生成唯一的解决方案名。  
  
     \- 或 \-  
  
     检查确保解决方案名不包含前导空格或尾部空格并且不是保留字。  保留字包括 NUL、CON、AUX、COM*x* 或 LPT*x*，其中 *x* 为 1\-9 的数字。  
  
## 请参阅  
 [“命令”窗口](../Topic/Command%20Window.md)