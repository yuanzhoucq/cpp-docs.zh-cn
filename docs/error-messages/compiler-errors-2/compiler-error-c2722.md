---
title: 编译器错误 C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 4274ac6ec33e0176f998fcf5a2b3efd570a4009f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546258"
---
# <a name="compiler-error-c2722"></a>编译器错误 C2722

:: 运算符： 非法的后缀运算符命令;使用 operator operator

`operator`语句一些专门选出`::new`或`::delete`。 `new`并`delete`运算符是全局的因此范围解析运算符 (`::`) 没有任何意义。 删除 `::` 运算符。