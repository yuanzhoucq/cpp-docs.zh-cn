---
title: 链接器工具错误 LNK1164 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b07dcf360a58b07b84abe655641b758d6137d0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087420"
---
# <a name="linker-tools-error-lnk1164"></a>链接器工具错误 LNK1164

部分节对齐 （数字） 大于 /ALIGN 值

对象文件中的给定部分的对齐大小超出了与指定的值[/align](../../build/reference/align-section-alignment.md)选项。 **/Align**值必须是 2 的幂和必须等于或超过对象文件中提供的部分对齐方式。

重新编译，使用较小的部分对齐方式或增加 **/align**值。