---
title: 编译器警告 （等级 1） C4276 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afedab27c2fb93075aa33053c12ec6973824f144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4276"></a>编译器警告（等级 1）C4276
function： 不提供原型;假定没有参数  
  
 当你执行与函数的地址[__stdcall](../../cpp/stdcall.md)调用约定，你必须提供原型，以便编译器可以创建函数的修饰的名称。 由于*函数*不具有任何原型，编译器，创建修饰的名时，假定函数没有任何参数。