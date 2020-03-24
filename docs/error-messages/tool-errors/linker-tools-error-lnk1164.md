---
title: 链接器工具错误 LNK1164
ms.date: 11/04/2016
f1_keywords:
- LNK1164
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
ms.openlocfilehash: 5f32fbd455faff449f57cfb9bb38009b03005913
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184029"
---
# <a name="linker-tools-error-lnk1164"></a>链接器工具错误 LNK1164

节部分对齐方式（数字）大于/ALIGN 值

对象文件中给定部分的对齐大小超过了用[/align](../../build/reference/align-section-alignment.md)选项指定的值。 **/Align**值必须是2的幂，并且必须等于或大于对象文件中给定的节对齐方式。

使用较小的节对齐进行重新编译，或增加 **/align**值。
