---
title: "文件的打开模式未设置为有效值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 969541f6-9ff6-4804-ba61-0d17370060ef
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 文件的打开模式未设置为有效值
为文件的打开模式提供的值无效。 下表显示 <xref:Microsoft.VisualBasic.OpenMode> 枚举的有效值。  
  
|值|模式|  
|-------|--------|  
|1|`OpenMode.Input`|  
|2|`OpenMode.Output`|  
|4|`OpenMode.Random`|  
|8|`OpenMode.Append`|  
|32|`OpenMode.Binary`|  
  
### 更正此错误  
  
-   验证为文件的打开模式提供的值。  
  
## 请参阅  
 [NOTINBUILD OpenMode 枚举](http://msdn.microsoft.com/zh-cn/e995bd42-d11f-455c-88c4-308345172633)   
 [My.Computer.FileSystem 对象](../Topic/My.Computer.FileSystem%20Object.md)   
 [从文件读取](../Topic/Reading%20from%20Files%20in%20Visual%20Basic.md)   
 [写入文件](../Topic/Writing%20to%20Files%20in%20Visual%20Basic.md)