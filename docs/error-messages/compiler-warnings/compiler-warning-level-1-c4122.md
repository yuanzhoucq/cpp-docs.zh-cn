---
title: 编译器警告（等级 1）C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: a01899de643a1f10f2211a67025fd3f46c546b8a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176320"
---
# <a name="compiler-warning-level-1-c4122"></a>编译器警告（等级 1）C4122

“function”: alloc_text 仅适用于带 C 链接的函数

**alloc_text** 杂注仅适用于使用 **extern c**声明的函数。 它不能与外部 C++ 函数一起使用。

将忽略杂注。
