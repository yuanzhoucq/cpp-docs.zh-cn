---
title: 编译器警告（等级 1）C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: c10b19b39fcb40527c9e9276f47ecff42ca5a643
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280381"
---
# <a name="compiler-warning-level-1-c4711"></a>编译器警告（等级 1）C4711

为内联展开选定了函数“function”

编译器在上执行给定的函数，尽管它没有标记为内联。

如果启用 C4711 [/ob2](../../build/reference/ob-inline-function-expansion.md)指定。

在由编译器自行执行内联。 此警告为信息性。

默认情况下，此警告处于关闭状态。 若要启用警告，请使用[#pragma 警告](../../preprocessor/warning.md)。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。