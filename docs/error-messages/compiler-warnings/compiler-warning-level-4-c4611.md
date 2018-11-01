---
title: 编译器警告（等级 4）C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542306"
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611

function 和 c + + 对象析构之间的交互是不可移植

在某些平台，包括的函数上**捕获**可能不支持析构时超出范围的 c + + 对象语义。

若要避免未知的行为，应避免使用**捕获**具有构造函数和析构函数的函数中。

仅一次; 发出此警告请参阅[杂注警告](../../preprocessor/warning.md)。