---
title: 编译器错误 C2338
ms.date: 11/04/2016
f1_keywords:
- C2338
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
ms.openlocfilehash: c92a95b97cb4c57d3ad5cfbf8fe1d9980d5362cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221206"
---
# <a name="compiler-error-c2338"></a>编译器错误 C2338

> *错误消息*

此错误可能是 **`static_assert`** 编译期间出错引起的。 消息由 **`static_assert`** 参数提供。

此错误消息还可以由外部提供程序生成到编译器。 在大多数情况下，属性提供程序 DLL （如 ATLPROV）会报告这些错误。 此消息的一些常见形式包括：

- "*attribute*" Atl 特性提供程序：错误 Atl*编号**消息*

- 特性 "*attribute*" 的用法不正确

- "*用法*"：特性 "usage" 的格式不正确

这些错误通常是不可恢复的，并且可能会出现严重的编译器错误。

若要解决这些问题，请更正属性用法。 例如，在某些情况下，必须先声明特性参数，然后才能使用这些参数。 如果提供了 ATL 错误号，请查看有关该错误的文档以了解更多特定信息。
