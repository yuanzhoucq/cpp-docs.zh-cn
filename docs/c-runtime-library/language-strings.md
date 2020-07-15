---
title: Language Strings
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 7713fe3f7cff4b80ce72927fa970e03914f94346
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373599"
---
# <a name="language-strings"></a>Language Strings

[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 函数均可在不使用 Unicode 代码页的操作系统上使用 Windows NLS API 支持的语言。 有关操作系统版本支持的语言的列表，请参阅[附录 a：](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)以 MS-LCID 显示的产品行为 \[ ]： Windows 语言代码标识符（LCID）参考。 语言字符串可以是支持语言列表的“语言”**** 和“语言标记”**** 列中的任意值。 有关枚举可用区域设置名称和相关值的代码示例，请参阅 [NLS：基于名称的 API 示例](/windows/win32/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-language-strings"></a>其他受支持的语言字符串

Microsoft C 运行时库实现还支持下面这些语言字符串：

|语言字符串|等效区域设置名称|
|---------------------|----------------------------|
|美国|en-US|
|american english|en-US|
|american-english|en-US|
|澳大利亚|en-AU|
|比利时|nl-BE|
|加拿大|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|中国|zh|
|chinese-hongkong|zh-HK|
|chinese-simplified|zh-CN|
|chinese-singapore|zh-SG|
|chinese-traditional|zh-TW|
|dutch-belgian|nl-BE|
|english-american|en-US|
|english-aus|en-AU|
|english-belize|en-BZ|
|english-can|en-CA|
|english-caribbean|en-029|
|english-ire|en-IE|
|english-jamaica|en-JM|
|english-nz|en-NZ|
|english-south africa|en-ZA|
|english-trinidad y tobago|en-TT|
|english-uk|en-GB|
|english-us|en-US|
|english-usa|en-US|
|french-belgian|fr-BE|
|french-canadian|fr-CA|
|french-luxembourg|fr-LU|
|french-swiss|fr-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|german-luxembourg|de-LU|
|german-swiss|de-CH|
|irish-english|en-IE|
|italian-swiss|it-CH|
|挪威|否|
|norwegian-bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|portuguese-brazilian|pt-BR|
|spanish-argentina|es-AR|
|spanish-bolivia|es-BO|
|spanish-chile|es-CL|
|spanish-colombia|es-CO|
|spanish-costa rica|es-CR|
|spanish-dominican republic|es-DO|
|spanish-ecuador|es-EC|
|spanish-el salvador|es-SV|
|spanish-guatemala|es-GT|
|spanish-honduras|es-HN|
|spanish-mexican|es-MX|
|spanish-modern|es-ES|
|spanish-nicaragua|es-NI|
|spanish-panama|es-PA|
|spanish-paraguay|es-PY|
|spanish-peru|es-PE|
|spanish-puerto rico|es-PR|
|spanish-uruguay|es-UY|
|spanish-venezuela|es-VE|
|swedish-finland|sv-FI|
|瑞士|de-CH|
|uk|en-GB|
|us|en-US|
|usa|en-US|

## <a name="see-also"></a>另请参阅

[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[国家/地区字符串](../c-runtime-library/country-region-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
