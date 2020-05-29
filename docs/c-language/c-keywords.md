---
title: C 关键字
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: e1364e0edacd94efa4ade6c6892a57d619635a39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326789"
---
# <a name="c-keywords"></a>C 关键字

“关键字”是对 C 编译器具有特殊含义的单词。 在翻译的第 7 和第 8 阶段中，标识符不能具有与 C 关键字相同的拼写和大小写。 （请参阅《预处理器参考》  中的[翻译阶段](../preprocessor/phases-of-translation.md)的说明；有关标识符的信息，请参阅[标识符](../c-language/c-identifiers.md)。）C 语言使用下列关键字：

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**case**|**enum**|**register**|**typedef**|
|**char**|**extern**|**return**|**union**|
|**const**|**float**|**short**|**unsigned**|
|**continue**|**for**|**signed**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

您不能重新定义关键字。 但是，你可在使用 C [预处理器指令](../preprocessor/preprocessor-directives.md)编译之前指定关键字的替换文本。

**Microsoft 专用**

ANSI C 标准允许为了编译器实现保留带有两个前导下划线的标识符。 因此，Microsoft 约定的是在 Microsoft 专用关键字名称前放置双下划线。 这些单词不能用作标识符名称。 有关命名标识符的 ANSI 规则的描述，包括双下划线的使用，请参阅[标识符](../c-language/c-identifiers.md)。

下列关键字和特殊标识符由 Microsoft C 编译器识别：

|||||
|-|-|-|-|
|**__asm**<sup>3</sup>|**dllimport**<sup>2</sup>|**__int8**<sup>3</sup>|**naked**<sup>2</sup>|
|**__based**<sup>1, 3</sup>|**__except**<sup>3</sup>|**__int16**<sup>3</sup>|**__stdcall**<sup>3</sup>|
|**__cdecl**<sup>3</sup>|**__fastcall**|**__int32**<sup>3</sup>|**thread**<sup>2</sup>|
|**__declspec**<sup>3</sup>|**__finally**<sup>3</sup>|**__int64**<sup>3</sup>|**__try**<sup>3</sup>|
|**dllexport**<sup>2</sup>|**__inline**<sup>3</sup>|**__leave**<sup>3</sup>||

<sup>1</sup> **__based** 关键字对于 32 位和 64 位目标编译的使用会受到限制。

<sup>2</sup> 这些关键字在与 **__declspec** 一起使用时是特殊标识符；它们在其他上下文中的使用不受限制。

<sup>3</sup> 为了与早期版本兼容，这些关键字在启用 Microsoft 扩展时可同时适用于两个前导下划线和单个前导下划线。

默认情况下将启用 Microsoft 扩展。 若要确保你的程序是完全可移植的，可通过在编译期间指定 [/Za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)选项来禁用 Microsoft 扩展。 如果这样做，将禁用某些 Microsoft 专用关键字。

启用 Microsoft 扩展时，您可在程序中使用上面列出的关键字。 为了兼容 ANSI，这其中大部分关键字以一个双下划线开头。 **dllexport**、**dllimport**、**naked** 和 **thread** 这 4 个关键字除外，它们仅与 **__declspec** 一起使用，因此无需前导双下划线。 为了向后兼容，支持其余的关键字的单下划线版本。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 的元素](../c-language/elements-of-c.md)
