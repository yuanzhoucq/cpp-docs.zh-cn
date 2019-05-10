---
title: 编译器警告（等级 4）C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349667"
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611

function 之间的交互和C++对象析构是不可移植

在某些平台，包括的函数上**捕获**可能不支持C++对象超出范围时析构的语义。

若要避免未知的行为，应避免使用**捕获**具有构造函数和析构函数的函数中。

仅一次; 发出此警告请参阅[杂注警告](../../preprocessor/warning.md)。