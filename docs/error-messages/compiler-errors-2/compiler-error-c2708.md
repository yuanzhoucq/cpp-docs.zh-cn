---
title: 编译器错误 C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460068"
---
# <a name="compiler-error-c2708"></a>编译器错误 C2708

identifier： 以字节为单位的实际参数长度不同于上一个调用或引用

一个[__stdcall](../../cpp/stdcall.md)函数前面必须是原型。 否则为编译器将解释为对作为原型函数的第一个调用，并且当编译器遇到不匹配的调用时发生此错误。

若要解决此错误，请添加一个函数原型。