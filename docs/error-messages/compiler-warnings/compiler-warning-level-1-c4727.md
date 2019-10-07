---
title: 编译器警告（等级 1）C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 1bcc029536d2602d50178d7148332b8371db3c7f
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630834"
---
# <a name="compiler-warning-level-1-c4727"></a>编译器警告（等级 1）C4727

在 obj_file_1 和 obj_file_2 中找到具有相同时间戳的名为 pch_file 的 PCH。  使用第一个 PCH。

> [!NOTE]
> 在 Visual Studio 2017 及更早版本中, 预编译标头默认称为*stdafx.h* , 在 Visual studio 2019 和更高版本中, 默认情况下, 它称为 " *.pch* "。

用 **/yc**编译多个 compiland 时, 以及编译器能够用同一 .pch 时间戳标记所有 .obj 文件时, 会发生 C4727。

若要解决此问题, 请使用 **/yc/c** (创建 pch) 编译一个源文件, 并使用 **/yu/c**单独进行编译 (使用 pch), 然后将它们链接在一起。

如果执行了以下操作, 则会生成 C4727:

::: moniker range="<=vs-2017"

**cl/clr/GL a .cpp b./Ycstdafx。h**

您可以改为执行以下操作:

**cl/clr/GL a .cpp/Ycstdafx.h/c**

**cl/clr/GL b. .cpp/Yustdafx.h/link a .obj**

::: moniker-end

::: moniker range=">=vs-2019"

**cl/clr/GL a .cpp b./Ycpch。h**

您可以改为执行以下操作:

**cl/clr/GL a .cpp/Ycpch.h/c**

**cl/clr/GL b. .cpp/Yupch.h/link a .obj**

::: moniker-end


有关详细信息，请参见

- [/Yc（创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu（使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)