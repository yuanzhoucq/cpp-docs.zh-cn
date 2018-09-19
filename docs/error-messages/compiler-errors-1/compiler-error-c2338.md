---
title: 编译器错误 C2338 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77bc98afdad36e0505abb58ee06ec1c7e7654ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071570"
---
# <a name="compiler-error-c2338"></a>编译器错误 C2338

> *错误消息*

此错误可能引起`static_assert`编译过程中的出错。 该消息提供的`static_assert`参数。

此外可以通过向编译器的外部提供程序生成此错误消息。 在大多数情况下，这些错误由特性提供程序 DLL，如 ATLPROV 进行报告。 此消息的一些常见形式包括：

> '*特性*Atl 特性提供程序： 错误 ATL*数量**消息*

> 属性的用法不正确*特性*

> '*使用情况*： 特性用途的格式不正确

这些错误通常是不可恢复，并可能跟一个严重的编译器错误。

若要解决这些问题，请更正属性用法。 例如，在某些情况下，特性参数必须声明才可以使用。 如果提供 ATL 错误号，则检查该错误以了解更多特定信息的文档。
