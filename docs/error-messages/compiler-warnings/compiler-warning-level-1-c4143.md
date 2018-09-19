---
title: 编译器警告 （等级 1） C4143 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4143
dev_langs:
- C++
helpviewer_keywords:
- same_seg
- C4143
ms.assetid: ef0bd19f-d169-4034-8710-b22971bd642d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31124c4d8040c0c2d602225e42b55bcc311f1b18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072857"
---
# <a name="compiler-warning-level-1-c4143"></a>编译器警告（等级 1）C4143

不支持杂注“same_seg”；使用 __based 分配

**#Pragma same_seg** 不再受支持。 请改用 [__based](../../cpp/based-pointers-cpp.md) 关键字。