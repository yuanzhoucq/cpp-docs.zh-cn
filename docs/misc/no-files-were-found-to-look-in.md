---
title: "No files were found to look in. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_FRLookInEmpty"
  - "vs.message.0x800A00DE"
ms.assetid: d560aef3-7a55-4fbb-a541-1a43fc13c18b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No files were found to look in.
当已在“查找范围”列表中指定文件名或目录，而该文件名或目录不存在或无法找到时，通常会发生此错误。  如果指定某个有效目录，而该目录不包含“文件类型”列表中所指定的文件扩展名，或者该指定的目录中不包含任何文件，也会出现此错误。  如果在设置了 `Hidden` 或 `System` 特性的目录中进行搜索，则也会出现该错误。  
  
### 更正此错误  
  
1.  使用**自定义目录集**对话框浏览要搜索的目录或文件名，而不要键入路径或文件名。  通过选择**查找范围**列表旁边的省略号按钮，可访问**自定义目录集**对话框。  
  
2.  将在**文件类型**列表中指定的文件扩展名更改为 \*.\*，以搜索指定目录中的所有文件。  
  
### 跳过此错误  
  
1.  按住 Ctrl 键并按 ScrLk。  
  
     这将取消对话框。  
  
## 请参阅  
 [查找和替换文本](../Topic/Finding%20and%20Replacing%20Text.md)   
 [在文件中查找](../Topic/Find%20in%20Files.md)   
 [Choose Search Folders](http://msdn.microsoft.com/zh-cn/85af6458-dcde-4a84-9ea4-f5cc6550dc80)