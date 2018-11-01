---
title: 链接器工具错误 LNK1164
ms.date: 11/04/2016
f1_keywords:
- LNK1164
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
ms.openlocfilehash: 8685a9e0eb356719eaab129af9df9a1cc0ebb085
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585492"
---
# <a name="linker-tools-error-lnk1164"></a>链接器工具错误 LNK1164

部分节对齐 （数字） 大于 /ALIGN 值

对象文件中的给定部分的对齐大小超出了与指定的值[/align](../../build/reference/align-section-alignment.md)选项。 **/Align**值必须是 2 的幂和必须等于或超过对象文件中提供的部分对齐方式。

重新编译，使用较小的部分对齐方式或增加 **/align**值。