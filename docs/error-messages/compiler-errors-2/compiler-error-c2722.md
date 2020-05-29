---
title: 编译器错误 C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 7426df1970dee58cd4363ee345e2286165e375b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202157"
---
# <a name="compiler-error-c2722"></a>编译器错误 C2722

"：： operator"：非法的运算符命令;使用 "operator operator"

`operator` 语句重定义 `::new` 或 `::delete`。 `new` 和 `delete` 运算符是全局运算符，因此范围解析运算符（`::`）没有意义。 删除 `::` 运算符。
