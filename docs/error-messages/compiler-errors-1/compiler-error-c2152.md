---
title: 编译器错误 C2152
ms.date: 11/04/2016
f1_keywords:
- C2152
helpviewer_keywords:
- C2152
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
ms.openlocfilehash: 072b5f13a639b1bd3d8e028fcd6c811012bfa2bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175223"
---
# <a name="compiler-error-c2152"></a>编译器错误 C2152

identifier： 指向具有不同的属性的函数的指针

指向具有一个调用约定的函数的指针 (`__cdecl`， `__stdcall`，或`__fastcall`) 分配给到具有另一个调用约定的函数指针。