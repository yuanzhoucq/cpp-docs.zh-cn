---
title: assert 函数输出的诊断 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac5473a2dd592bbd9af2f65044d3d7d97515dc37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103381"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 函数输出的诊断

**ANSI 4.2** assert 函数输出的诊断和终止行为

如果表达式为 false (0)，则 assert 函数将输出诊断消息并调用 abort 例程。 诊断消息具有以下形式

> **Assertion failed**: expression **, file** filename **, line** linenumber

其中，filename 是源文件的名称，linenumber 是源文件中失败的断言的行号。 如果表达式为 true（非零），则不执行任何操作。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)