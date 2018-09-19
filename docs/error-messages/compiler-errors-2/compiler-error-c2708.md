---
title: 编译器错误 C2708 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0accd68881cccad5e34530a6c157a4e8179b283
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111090"
---
# <a name="compiler-error-c2708"></a>编译器错误 C2708

identifier： 以字节为单位的实际参数长度不同于上一个调用或引用

一个[__stdcall](../../cpp/stdcall.md)函数前面必须是原型。 否则为编译器将解释为对作为原型函数的第一个调用，并且当编译器遇到不匹配的调用时发生此错误。

若要解决此错误，请添加一个函数原型。