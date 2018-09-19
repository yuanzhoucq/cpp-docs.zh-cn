---
title: 编译器错误 C3180 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3180
dev_langs:
- C++
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e200a75164c0d7fdb0c6804d084630cc6e6007e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048365"
---
# <a name="compiler-error-c3180"></a>编译器错误 C3180

type name： 名称超出了 limit 个字符的元数据限制

编译器截断元数据中的托管类型的名称。 截断将使类型无法通过`#using`指令 （或另一种语言的等效项）。

类型名称限制包括任何命名空间限定。