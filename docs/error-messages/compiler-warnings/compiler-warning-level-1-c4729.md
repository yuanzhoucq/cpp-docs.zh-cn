---
title: 编译器警告（等级 1）C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: f5f93cadd97eefe0d6c6da97be99ec5fd82ece24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386390"
---
# <a name="compiler-warning-level-1-c4729"></a>编译器警告（等级 1）C4729

根据警告，函数对于流图形太大

当函数太大，不能用可靠的方法（如检查是否有将生成警告的情况）进行编译时生成此警告。 仅在使用 [/Od](../../build/reference/od-disable-debug.md) 编译器选项时生成此警告。

若要解决此警告，请将函数拆成较小的函数。