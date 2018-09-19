---
title: 编译器错误 C2722 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9138172bb108095c4e72407f1e17e8f4fa2370c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082659"
---
# <a name="compiler-error-c2722"></a>编译器错误 C2722

:: 运算符： 非法的后缀运算符命令;使用 operator operator

`operator`语句一些专门选出`::new`或`::delete`。 `new`并`delete`运算符是全局的因此范围解析运算符 (`::`) 没有任何意义。 删除`::`运算符。