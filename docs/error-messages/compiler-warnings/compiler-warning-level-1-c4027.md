---
title: 编译器警告 （等级 1） C4027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4027
dev_langs:
- C++
helpviewer_keywords:
- C4027
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b919eeece5529d1914fadf5724088e3e64e73db9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089510"
---
# <a name="compiler-warning-level-1-c4027"></a>编译器警告（等级 1）C4027

未用形参表声明的函数

函数声明没有形参，但在函数定义中有形参或在调用中有实参。 对此函数的后续调用假定该函数采用函数定义或调用中找到的类型的实参。