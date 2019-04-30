---
title: 编译器错误 C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367598"
---
# <a name="compiler-error-c2696"></a>编译器错误 C2696

无法创建临时对象的托管类型 type

对引用`const`非托管程序中会导致编译器调用构造函数，并在堆栈上创建临时对象。 但是，永远不会可以在堆栈上创建托管的类。

C2696 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
