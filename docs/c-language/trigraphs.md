---
title: "三字符组 | Microsoft Docs"
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
  - "? 符号, 三字符组"
  - "?? 三字符组"
  - "??' 三字符组"
  - "??- 三字符组"
  - "??! 三字符组"
  - "??) 三字符组"
  - "??/ 三字符组"
  - "??< 三字符组"
  - "??= 三字符组"
  - "??> 三字符组"
  - "问号, 在三字符组中"
  - "三字符组"
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 三字符组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 源程序的源字符集包含在 7 位 ASCII 字符集中，但它是 ISO 646\-1983 固定语言代码集的超集。  三元组序列仅允许使用 ISO（国际标准组织）固定语言代码集编写 C 程序。  三元组是三字符序列（由两个连续问号引入），编译器会将它替换为其相应的标点字符。  可以将 C 源文件中的三元组与不包含某些标点字符的方便图形表示形式的字符集一起使用。  
  
 下表显示了九个三元组序列。  第一列中的标点字符的源文件中的所有匹配项都将替换为第二列中的相应字符。  
  
### 三元组序列  
  
|三元组|标点字符|  
|---------|----------|  
|??\=|\#|  
|??\(|\[|  
|??\/|\\|  
|??\)|\]|  
|??'|^|  
|??\<|{|  
|??\!|&#124;|  
|??\>|}|  
|??\-|~|  
  
 三元组始终被视为单个源字符。  在识别字符串和字符常数中的转义符前，三元组的转换会在第一个[转换阶段](../preprocessor/phases-of-translation.md)出现。  仅识别上表中显示的九个三元组。  所有其他字符序列都未转换。  
  
 字符转义序列 **\\?** 可防止对类似于三元组的字符序列进行错误解释。（有关转义序列的信息，请参阅[转义序列](../c-language/escape-sequences.md)。）例如，如果您尝试打印具有 `printf` 语句的字符串 `What??!`  
  
```  
printf( "What??!\n" );  
```  
  
 打印的字符串为 `What|`，因为 `??!` 是一个三元组序列，它将替换为         `|` 字符。  编写如下语句以正确打印字符串：  
  
```  
printf( "What?\?!\n" );  
```  
  
 在此 `printf` 语句中，第二个问号的前面的反斜杠转义符可防止将 `??!` 错误解释为三元组。  
  
## 请参阅  
 [C 标识符](../c-language/c-identifiers.md)