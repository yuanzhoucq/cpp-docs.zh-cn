---
title: 数学错误 M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173655"
---
# <a name="math-error-m6202"></a>数学错误 M6202

"function"： _SING 错误

给定函数的参数是此函数的奇点值。 未为该参数定义函数。

此错误将调用具有函数名称、其参数和错误类型的 `_matherr` 函数。 您可以重写 `_matherr` 函数，以自定义对某些运行时浮点算术错误的处理。
