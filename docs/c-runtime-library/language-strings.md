---
title: Language Strings
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: a9e6eaa65516b5b49022526f24e220dec83b2c26
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500078"
---
# <a name="language-strings"></a>Language Strings

[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 函数均可在不使用 Unicode 代码页的操作系统上使用 Windows NLS API 支持的语言。 有关操作系统版本支持的语言列表，请参阅[附录 A：产品行为](https://msdn.microsoft.com/library/cc233982.aspx)（位于 [MS-LCID]：Windows 语言代码标识符 (LCID) 参考内）。 语言字符串可以是支持语言列表的“语言”  和“语言标记”  列中的任意值。 有关枚举可用区域设置名称和相关值的代码示例，请参阅 [NLS：基于名称的 API 示例](/windows/win32/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-language-strings"></a>其他受支持的语言字符串

Microsoft C 运行时库实现还支持下面这些语言字符串：

|语言字符串|等效区域设置名称|
|---------------------|----------------------------|
|american|en-US|
|american english|en-US|
|american-english|en-US|
|australian|en-AU|
|belgian|nl-BE|
|canadian|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|chinese|zh|
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
|norwegian|否|
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
|swiss|de-CH|
|uk|en-GB|
|us|en-US|
|usa|en-US|

## <a name="see-also"></a>请参阅

[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[国家/地区字符串](../c-runtime-library/country-region-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
