---
title: 错误 C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 2b7f6fd878f0d0ba6cde19a3a316a01c390e954a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600594"
---
# <a name="fatal-error-c1382"></a>错误 C1382

由于在生成时 'obj' 重新生成 PCH 文件 file。 请重新生成此对象

使用时[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到比它指向 CIL.obj 的.pch 文件。 CIL.obj 文件中的信息已过期。 重新生成对象。

如果使用进行编译，也可能发生 C1382 **/Yc**，但还将多个源的代码文件传递给编译器。  若要解决，不要使用 **/Yc**向编译器传递多个源的代码文件时。  有关详细信息，请参阅[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)。