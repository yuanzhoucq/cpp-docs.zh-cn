---
title: 编译器错误 C2095
ms.date: 11/04/2016
f1_keywords:
- C2095
helpviewer_keywords:
- C2095
ms.assetid: 44f8ada1-974f-4e81-a408-33ac6695aa53
ms.openlocfilehash: 327f4406be241f3aff89fd357fc103398401ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207657"
---
# <a name="compiler-error-c2095"></a>编译器错误 C2095

"function"：实参具有 "void" 类型：参数 "number"

传递给函数的参数是类型 `void`，这是不允许的。 改为使用指向 void （`void *`）的指针。

`number` 指示 `void`哪个参数。
