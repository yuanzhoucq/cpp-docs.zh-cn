---
title: 编译器错误 C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 567c92ddabbe2517700e4c67ef2c1ba899baada8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200663"
---
# <a name="compiler-error-c3552"></a>编译器错误 C3552

“typename”: 后指定返回类型不能包含“auto”

如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 但是，不能使用其他 `auto` 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。

`auto myFunction->auto; // C3552`
