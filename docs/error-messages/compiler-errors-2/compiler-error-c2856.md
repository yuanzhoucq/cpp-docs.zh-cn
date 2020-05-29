---
title: 编译器错误 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: c88610607083ecfaf5f20cd585b479991fa51b44
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201866"
---
# <a name="compiler-error-c2856"></a>编译器错误 C2856

\#pragma hdrstop 不能在 #if 块内

不能将 `hdrstop` 杂注放置在条件编译块的正文内。

将 `#pragma hdrstop` 语句移动到 `#if/#endif` 块中未包含的区域。
