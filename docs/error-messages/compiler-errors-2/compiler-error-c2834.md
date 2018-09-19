---
title: 编译器错误 C2834 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b94e1a3fba9bc3589af020340651b4546347cf1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089334"
---
# <a name="compiler-error-c2834"></a>编译器错误 C2834

operator operator 必须是全局限定

`new`和`delete`运算符被绑定到类驻留位置。 不能使用范围解析的某个版本`new`或`delete`从另一个类。 若要实现的多个窗体`new`或`delete`运算符，用额外的形参创建运算符版本。