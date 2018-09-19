---
title: 编译器警告 （等级 C4611 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 723976dc8b7085ede9b3157445ff3026de6fc4b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091044"
---
# <a name="compiler-warning-level-4-c4611"></a>编译器警告（等级 4）C4611

function 和 c + + 对象析构之间的交互是不可移植

在某些平台，包括的函数上**捕获**可能不支持析构时超出范围的 c + + 对象语义。

若要避免未知的行为，应避免使用**捕获**具有构造函数和析构函数的函数中。

仅一次; 发出此警告请参阅[杂注警告](../../preprocessor/warning.md)。