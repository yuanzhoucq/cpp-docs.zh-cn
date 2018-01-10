---
title: "国家/地区字符串 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94ad99ebd05fa9e37a56f2e12818f30f1f4b1212
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="countryregion-strings"></a>Country/Region Strings
可以将国家和地区字符串与语言字符串结合使用，以便创建 `setlocale`、 `_wsetlocale`、 `_create_locale`和 `_wcreate_locale` 函数的区域设置规范。 有关各种 Windows 操作系统版本支持的国家/地区名称列表，请参阅[国家语言支持 (NLS) API 参考](https://www.microsoft.com/resources/msdn/goglobal/default.mspx)。 在列表中，国家/地区字符串可以是“区域设置 - 语言国家/地区”列中的任何国家/地区值，或“国家或地区名称缩写”列中的任何缩写。 有关 Windows 操作系统（按版本）中的其他语言支持信息，请参阅“[MS-LCID]：Windows 语言代码标识符 (LCID) 参考”中的[附录 A：产品行为](http://msdn.microsoft.com/goglobal/bb896001.aspx)。  
  
 C 运行时库实现还支持以下其他国家/地区字符串和缩写：  
  
|国家/地区字符串|缩写|等效区域设置名称|  
|----------------------------|------------------|----------------------------|  
|america|USA|en-US|  
|britain|GBR|en-GB|  
|china|CHN|zh-CN|  
|czech|CZE|cs-CZ|  
|england|GBR|en-GB|  
|great britain|GBR|en-GB|  
|holland|NLD|nl-NL|  
|hong-kong|HKG|zh-HK|  
|new-zealand|NZL|en-NZ|  
|nz|NZL|en-NZ|  
|pr china|CHN|zh-CN|  
|pr-china|CHN|zh-CN|  
|puerto-rico|PRI|es-PR|  
|slovak|SVK|sk-SK|  
|south africa|ZAF|af-ZA|  
|south korea|KOR|ko-KR|  
|south-africa|ZAF|af-ZA|  
|south-korea|KOR|ko-KR|  
|trinidad & tobago|TTO|en-TT|  
|uk|GBR|en-GB|  
|united-kingdom|GBR|en-GB|  
|united-states|USA|en-US|  
|us|USA|en-US|  
  
## <a name="see-also"></a>请参阅  
 [区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [语言字符串](../c-runtime-library/language-strings.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)