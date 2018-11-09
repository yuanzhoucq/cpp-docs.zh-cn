---
title: 数据类型映射
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 3d6e43d8d39cb208efbb6010ef2591a2880fd584
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647887"
---
# <a name="data-type-mappings"></a>数据类型映射

TCHAR.H 中定义了这些数据类型映射，具体取决于程序中是否定义了常量 `_UNICODE` 或 `_MBCS`。

有关相关信息，请参阅[将 TCHAR.H 数据类型用于 _MBCS 代码](../text/using-tchar-h-data-types-with-mbcs-code.md)。

### <a name="generic-text-data-type-mappings"></a>一般文本数据类型映射

|一般文本<br /><br /> 数据类型名|SBCS（_UNICODE、<br /><br /> _MBCS 未<br /><br /> 定义）|_MBCS<br /><br /> 已定义|_UNICODE<br /><br /> 已定义|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` 或 `_TEXT`|无效果（由预处理器删除）|无效果（由预处理器删除）|`L`（将以下字符或字符串转换为其 Unicode 对应项）|

## <a name="see-also"></a>请参阅

[一般文本映射](../c-runtime-library/generic-text-mappings.md)<br/>
[常量和全局变量映射](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[例程映射](../c-runtime-library/routine-mappings.md)<br/>
[示例一般文本程序](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[使用一般文本映射](../c-runtime-library/using-generic-text-mappings.md)