---
title: 编译器警告（等级 4）C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395165"
---
# <a name="compiler-warning-level-4-c4718"></a>编译器警告（等级 4）C4718

“function call”：递归调用无副作用，正在删除

函数包含递归调用，但却没有副作用。 正在删除对此函数的调用。 不影响程序的正确性，而是影响其行为。 但保留该调用会导致运行时堆栈溢出异常，请删除该调用，从而排除这种可能性。