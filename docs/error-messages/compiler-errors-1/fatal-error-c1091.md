---
title: 错误 C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 9758d4b779f4727012041da60632bcea8ce18d42
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624956"
---
# <a name="fatal-error-c1091"></a>错误 C1091

编译器限制：字符串长度超过“length”个字节

字符串常量超过当前的字符串长度限制。

你可能希望将静态字符串拆分为两个（或更多）变量，以及使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 在声明或在运行时联接结果。