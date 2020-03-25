---
title: 表达式计算器错误 CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184419"
---
# <a name="expression-evaluator-error-cxx0065"></a>表达式计算器错误 CXX0065

变量需要堆栈帧

表达式包含当前范围内存在但尚未创建的变量。

当你逐步进入函数的 prolog 但尚未设置该函数的堆栈帧时，或者如果你逐步进入函数的退出代码，就会出现此错误。

单步执行序言代码，直到在计算表达式之前设置了堆栈帧。

此错误与 CAN0065 相同。
