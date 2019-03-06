---
title: null 宏和未定义的宏
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: cf2dce2132cc1e7065cb0b93f1debd403f7a8342
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417224"
---
# <a name="null-and-undefined-macros"></a>null 宏和未定义的宏

Null 和未定义宏展开为空字符串，但定义为一个 null 字符串的宏被视为预处理表达式中定义。 若要定义宏为 null 的字符串，指定没有字符后在命令行或命令文件中的等号 （=） 除外的空格或制表符和将 null 字符串或定义括在双引号 ("")。 若要取消定义宏，请使用 **！UNDEF。** 有关详细信息，请参阅[生成文件预处理指令](../build/makefile-preprocessing-directives.md)。

## <a name="see-also"></a>请参阅

[定义 NMAKE 宏](../build/defining-an-nmake-macro.md)
