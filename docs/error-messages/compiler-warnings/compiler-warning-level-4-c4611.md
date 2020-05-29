---
title: 编译器警告（等级 4）C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198297"
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611

"function" 与C++对象析构之间的交互是不可移植的

在某些平台上，包含**catch**的函数在超出C++范围时可能不支持析构的对象语义。

若要避免意外的行为，请避免在具有构造函数和析构函数的函数中使用**catch** 。

此警告只发出一次;请参阅[杂注警告](../../preprocessor/warning.md)。
