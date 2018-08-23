---
title: 国家/地区字符串 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f227feec25e3b487772f8e469651f08be825419f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605625"
---
# <a name="countryregion-strings"></a>Country/Region Strings

可以将国家和地区字符串与语言字符串结合使用，以便创建 `setlocale`、 `_wsetlocale`、 `_create_locale`和 `_wcreate_locale` 函数的区域设置规范。 有关各种 Windows 操作系统版本支持的国家和地区名称列表，请转到“[MS-LCID]：Windows 语言代码标识符 (LCID) 参考”中的[附录 A：产品行为](https://msdn.microsoft.com/library/cc233982.aspx)，参阅其中表内的“语言”、“位置”和“语言标记”列。 有关枚举可用区域设置名称和相关值的代码示例，请参阅 [NLS：基于名称的 API 示例](/windows/desktop/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-country-and-region-strings"></a>其他受支持的国家和地区字符串

Microsoft C 运行时库实现还支持以下其他国家/地区字符串和缩写：

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
