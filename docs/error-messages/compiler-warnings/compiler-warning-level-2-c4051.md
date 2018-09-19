---
title: 编译器警告 （等级 2） C4051 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4051
dev_langs:
- C++
helpviewer_keywords:
- C4051
ms.assetid: 8c964e70-df12-45ff-93b9-496ad4271191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5074ca6f048aec06f98b6081d932ee85868cb9d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103396"
---
# <a name="compiler-warning-level-2-c4051"></a>编译器警告（等级 2）C4051

类型转换；可能丢失数据

表达式包含具有不同的基类型的两个数据项。 转换一个类型导致数据项被截断。

如果将数据项强制转换为适当的类型，则可能会修复此警告。