---
title: 编译器错误 C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562860"
---
# <a name="compiler-error-c2696"></a>编译器错误 C2696

无法创建临时对象的托管类型 type

对引用`const`非托管程序中会导致编译器调用构造函数，并在堆栈上创建临时对象。 但是，永远不会可以在堆栈上创建托管的类。

C2696 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
