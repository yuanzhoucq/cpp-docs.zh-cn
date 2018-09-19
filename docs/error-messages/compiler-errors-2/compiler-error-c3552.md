---
title: 编译器错误 C3552 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd9f7ae37500e115fa33fa61298cab800c88f9c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081255"
---
# <a name="compiler-error-c3552"></a>编译器错误 C3552

“typename”: 后指定返回类型不能包含“auto”

如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 但是，不能使用其他 `auto` 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。

`auto myFunction->auto; // C3552`