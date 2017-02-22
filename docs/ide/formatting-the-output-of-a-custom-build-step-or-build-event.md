---
title: "设置自定义生成步骤或生成事件输出的格式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成事件 [C++], 输出格式"
  - "生成步骤 [C++], 输出格式"
  - "builds [C++], 生成事件"
  - "builds [C++], 自定义生成步骤"
  - "自定义生成步骤 [C++], 输出格式"
  - "事件 [C++], 生成"
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 设置自定义生成步骤或生成事件输出的格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果正确设置了自定义生成步骤或生成事件输出的格式，则会给用户带来以下利益：  
  
-   在**“输出”**窗口中对警告和错误计数。  
  
-   输出出现在**“任务列表”**窗口中。  
  
-   在**“输出”**窗口中单击输出将显示适当的主题。  
  
-   在**“任务列表”**或**“输出”**窗口中启用 F1 操作。  
  
 输出的格式应该为：  
  
 {*filename* \(*line\#* \[, *column\#*\]\) &#124; *toolname*} **:**  
  
 \[*any text*\] {**error** &#124; **warning**} *code\#\#\#\#***:** *localizable string*  
  
 \[ *any text* \]  
  
 其中：  
  
-   {*a* &#124; *b*} 是 *a*或者 *b*的一个选项。  
  
-   \[`ccc`\] 为可选字符串或参数。  
  
 例如：  
  
 C:\\*sourcefile.cpp*\(134\) : error C2143: syntax error : missing ';' before '}'  
  
 链接：错误 LNK1104:无法打开文件 '*somelib.lib*"  
  
## 请参阅  
 [了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)