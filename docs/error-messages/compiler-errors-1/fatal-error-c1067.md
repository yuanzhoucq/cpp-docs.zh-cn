---
title: 错误 C1067 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f267e58617fbc68835fd3a387c4b635de4fd0530
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077667"
---
# <a name="fatal-error-c1067"></a>错误 C1067

编译器限制： 超出了大小类型记录的 64k 限制

如果符号的修饰的名超过 247 个字符，则可能发生此错误。  若要解决，缩短的符号名称。

当编译器生成调试信息时，它会发出类型记录，定义在源代码中遇到的类型。  例如，类型记录包含简单的结构和函数的自变量列表。  这些类型记录的一些可能是大型列表。

任何类型的记录的大小没有 64k 的限制。  如果超出该 64k 的限制，则将发生此错误。

如果有多个符号具有长名称或某个类、 结构或联合具有太多的成员，也可能发生 C1067。