---
title: 编译器警告（等级 1）C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586909"
---
# <a name="compiler-warning-level-1-c4276"></a>编译器警告（等级 1）C4276

function： 不提供原型;假定无参数

执行的函数的地址时[__stdcall](../../cpp/stdcall.md)调用约定，您必须提供原型，以便编译器可以创建函数的修饰的名。 由于*函数*具有的原型，编译器创建的修饰的名时，假定函数没有任何参数。