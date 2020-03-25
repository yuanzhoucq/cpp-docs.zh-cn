---
title: 错误 C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204342"
---
# <a name="fatal-error-c1067"></a>错误 C1067

编译器限制：已超出类型记录的64K 大小限制

如果符号的修饰名超过247个字符，则会出现此错误。  若要解决此问题，请缩短符号名称。

当编译器生成调试信息时，它会发出类型记录以定义在源代码中遇到的类型。  例如，类型记录包括函数的简单结构和参数列表。  其中一些类型记录可能是大型列表。

对于任何类型记录，都有64K 的大小限制。  如果超过64K 的限制，则会出现此错误。

如果有很多带有长名称的符号，或者类、结构或联合的成员太多，也可能会发生 C1067。
