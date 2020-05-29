---
title: 数学错误 M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 371a6c673826c6ce71d7a0eb3b9e08d9488f53f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193688"
---
# <a name="math-error-m6203"></a>数学错误 M6203

"function"： _OVERFLOW 错误

给定函数的结果太大，无法表示。

此错误将调用具有函数名称、其参数和错误类型的 `_matherr` 函数。 您可以重写 `_matherr` 函数，以自定义对某些运行时浮点算术错误的处理。
