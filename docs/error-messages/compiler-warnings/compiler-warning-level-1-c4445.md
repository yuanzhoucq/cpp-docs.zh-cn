---
title: 编译器警告 （等级 1） C4445 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4445
dev_langs:
- C++
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80b3e13f0f7271a38d71c65efa65f104e44aa475
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079942"
---
# <a name="compiler-warning-level-1-c4445"></a>编译器警告（等级 1）C4445

“function”: 在 WinRT 或托管类型中，虚方法不能为私有方法

如果虚函数是私有函数，则它无法由派生类型访问。 若要修复此错误，请将虚拟成员函数的可访问性更改为受保护或公共。