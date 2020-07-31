---
title: 编译器错误 C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: d2d3a60fcd4a26238cd6cf330f47b48c5b3198ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230826"
---
# <a name="compiler-error-c3552"></a>编译器错误 C3552

“typename”: 后指定返回类型不能包含“auto”

如果使用 **`auto`** 关键字作为函数返回类型的占位符，则必须提供一个后期指定的返回类型。 但是，不能使用其他 **`auto`** 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。

`auto myFunction->auto; // C3552`
