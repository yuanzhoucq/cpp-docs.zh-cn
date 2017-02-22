---
title: "语言字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "语言字符串"
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 语言字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`setlocale` 和 `_create_locale` 功能都可以使用操作系统中的 windows NLS API 支持语言而不需使用 Unicode 代码页。  有关以下操作系统版本所支持的语言的列表，请参见 [多区域语言支持 \(NLS\) API 引用](http://msdn.microsoft.com/goglobal/bb896001.aspx)。  语言字符串可以是所支持的语言列表栏中“语言”  和“语言名称缩写”  中的任何一个值。  C 运行时库的实现也支持这些语言字符串：  
  
|语言字符串|等效区域设置名称|  
|-----------|--------------|  
|american|en\-US|  
|american english|en\-US|  
|american\-english|en\-US|  
|australian|en\-AU|  
|belgian|nl\-BE|  
|canadian|en\-CA|  
|chh|zh\-HK|  
|chi|zh\-SG|  
|chinese|zh|  
|chinese\-hongkong|zh\-HK|  
|chinese\-simplified|zh\-CN|  
|chinese\-singapore|zh\-SG|  
|chinese\-traditional|zh\-TW|  
|dutch\-belgian|nl\-BE|  
|english\-american|en\-US|  
|english\-aus|en\-AU|  
|english\-belize|en\-BZ|  
|english\-can|en\-CA|  
|english\-caribbean|en\-029|  
|english\-ire|en\-IE|  
|english\-jamaica|en\-JM|  
|english\-nz|en\-NZ|  
|english\-south africa|en\-ZA|  
|english\-trinidad y tobago|en\-TT|  
|english\-uk|en\-GB|  
|english\-us|en\-US|  
|english\-usa|en\-US|  
|french\-belgian|fr\-BE|  
|french\-canadian|fr\-CA|  
|french\-luxembourg|fr\-LU|  
|french\-swiss|fr\-CH|  
|german\-austrian|de\-AT|  
|german\-lichtenstein|de\-LI|  
|german\-luxembourg|de\-LU|  
|german\-swiss|de\-CH|  
|爱尔兰英语|en\-IE|  
|意大利语瑞士|it\-CH|  
|挪威语|no|  
|挪威语 \- 博克马尔语|nb\-NO|  
|挪威语 \- 尼诺斯克语|nn\-NO|  
|巴西（葡萄牙语）|pt\-BR|  
|西班牙语 \- 阿根廷|es\-AR|  
|西班牙语 \- 玻利维亚|es\-BO|  
|西班牙语 \- 智利|es\-CL|  
|西班牙语 \- 哥伦比亚|es\-CO|  
|西班牙语 \- 哥斯达黎加|es\-CR|  
|西班牙语 \- 多米尼加共和国|es\-DO|  
|西班牙语 \- 多米尼加共和国|es\-EC|  
|西班牙语\(萨尔瓦多\)|es\-SV|  
|西班牙语 \- 危地马拉|es\-GT|  
|spanish\-honduras|es\-HN|  
|spanish\-mexican|es\-MX|  
|spanish\-modern|es\-ES|  
|spanish\-nicaragua|es\-NI|  
|spanish\-panama|es\-PA|  
|spanish\-paraguay|es\-PY|  
|spanish\-peru|es\-PE|  
|spanish\-puerto rico|es\-PR|  
|spanish\-uruguay|es\-UY|  
|spanish\-venezuela|es\-VE|  
|swedish\-finland|sv\-FI|  
|swiss|de\-CH|  
|uk|en\-GB|  
|us|en\-US|  
|usa|en\-US|  
  
## 请参阅  
 [区域设置名称、语言和国家\/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [国家\/地区字符串](../c-runtime-library/country-region-strings.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)