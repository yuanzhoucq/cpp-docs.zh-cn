---
title: "C 关键字 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fd746124cdfc267267bc5d6803700cca507c34d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-keywords"></a>C 关键字
“关键字”是对 C 编译器具有特殊含义的单词。 在翻译的第 7 和第 8 阶段中，标识符不能具有与 C 关键字相同的拼写和大小写。 （请参阅《预处理器参考》中的[翻译阶段](../preprocessor/phases-of-translation.md)的说明；有关标识符的信息，请参阅[标识符](../c-language/c-identifiers.md)。）C 语言使用下列关键字：  
  
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
|**__asm**|**dllimport**2|**__int8**|**naked**2|  
|**__based**1|**__except**|**__int16**|**__stdcall**|  
|**__cdecl**|**__fastcall**|**__int32**|**thread**2|  
|**__declspec**|**__finally**|**__int64**|**__try**|  
|**dllexport**2|**__inline**|**__leave**||  
  
 1. **__based** 关键字对于 32 位和 64 位目标编译的使用会受到限制。  
  
 2. 这些关键字在与 **__declspec** 一起使用时是特殊标识符；它们在其他上下文中的使用不受限制。  
  
 默认情况下将启用 Microsoft 扩展。 若要确保您的程序是完全可移植的，可通过在编译期间指定 /Za 选项（针对 ANSI 兼容性编译）来禁用 Microsoft 扩展。 如果这样做，将禁用 Microsoft 专用关键字。  
  
 启用 Microsoft 扩展时，您可在程序中使用上面列出的关键字。 为了兼容 ANSI，这其中大部分关键字以一个双下划线开头。 **dllexport**、**dllimport**、**naked** 和 **thread** 这 4 个关键字除外，它们仅与 **__declspec** 一起使用，因此无需前导双下划线。 为了向后兼容，支持其余的关键字的单下划线版本。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [C 的元素](../c-language/elements-of-c.md)