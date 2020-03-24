---
title: 编译器错误 C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 828e5bbca0b796864ec8b364ee69c18a3b5eea00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206943"
---
# <a name="compiler-error-c2170"></a>编译器错误 C2170

"identifier"：未声明为函数，不能是内部函数

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 杂注 `intrinsic` 用于除函数之外的项。

1. Pragma `intrinsic` 用于无内部形式的函数。
