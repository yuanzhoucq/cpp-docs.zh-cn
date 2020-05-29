---
title: 编译器错误 C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201876"
---
# <a name="compiler-error-c2834"></a>编译器错误 C2834

"operator operator" 必须是全局限定的

`new` 和 `delete` 运算符关联到它们所在的类。 范围解析不能用于从不同的类中选择 `new` 或 `delete` 的版本。 若要实现 `new` 或 `delete` 运算符的多种形式，请创建具有额外形参的运算符版本。
