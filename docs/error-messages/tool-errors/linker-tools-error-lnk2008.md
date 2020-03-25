---
title: 链接器工具错误 LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194819"
---
# <a name="linker-tools-error-lnk2008"></a>链接器工具错误 LNK2008

修正目标与 "symbol_name" 不对齐

LINK 在对象文件中找到了未正确对齐的链接地址目标。

此错误可能是由于自定义的 secton 对齐方式（例如 #pragma [pack](../../preprocessor/pack.md)）、 [align](../../cpp/align-cpp.md)修饰符或使用修改 secton 对齐的汇编语言代码引起的。

如果你的代码不使用上述任何一个，则这可能是由编译器导致的。
