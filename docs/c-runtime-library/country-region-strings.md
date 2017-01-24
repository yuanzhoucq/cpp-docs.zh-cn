---
title: "国家/地区字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "国家/地区字符串"
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 国家/地区字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以将国家和地区字符串与语言字符串结合使用，以便创建 `setlocale`、`_wsetlocale`、`_create_locale` 和 `_wcreate_locale` 函数的区域设置规范。 有关各种 Windows 操作系统版本支持的国家\/地区名称的列表，请参阅[区域语言支持 \(NLS\) API 参考](http://msdn.microsoft.com/goglobal/bb896001.aspx)。在列表中，国家\/地区字符串可以是“区域设置 \- 语言国家\/地区”列中的任何国家\/地区值，或“国家\/地区名称缩写”列中的任何缩写词。  
  
 C 运行时库实现还支持以下其他国家\/地区字符串和缩写：  
  
|国家\/地区字符串|缩写|等效区域设置名称|  
|---------------|--------|--------------|  
|america|USA|zh\-CN|  
|britain|GBR|en\-GB|  
|china|CHN|zh\-CN|  
|czech|CZE|cs\-CZ|  
|england|GBR|en\-GB|  
|great britain|GBR|en\-GB|  
|holland|NLD|nl\-NL|  
|hong\-kong|HKG|zh\-HK|  
|new\-zealand|NZL|en\-NZ|  
|nz|NZL|en\-NZ|  
|pr china|CHN|zh\-CN|  
|pr\-china|CHN|zh\-CN|  
|puerto\-rico|PRI|es\-PR|  
|slovak|SVK|sk\-SK|  
|south africa|ZAF|af\-ZA|  
|south korea|KOR|ko\-KR|  
|south\-africa|ZAF|af\-ZA|  
|south\-korea|KOR|ko\-KR|  
|trinidad & tobago|TTO|en\-TT|  
|uk|GBR|en\-GB|  
|united\-kingdom|GBR|en\-GB|  
|united\-states|USA|zh\-CN|  
|us|USA|zh\-CN|  
  
## 请参阅  
 [区域设置名称、语言和国家\/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [语言字符串](../c-runtime-library/language-strings.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)