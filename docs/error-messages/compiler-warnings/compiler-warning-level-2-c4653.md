---
title: 编译器警告 （等级 2） C4653 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4653
dev_langs:
- C++
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 376da24d4619eacc3e6b3defe8fdfc582800a898
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045973"
---
# <a name="compiler-warning-level-2-c4653"></a>编译器警告（等级 2）C4653

编译器选项 option 与预编译标头; 不一致忽略当前命令行选项

使用预编译标头指定的选项 ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) 选项，与创建预编译标头时指定的选项不一致。 此编译使用预编译标头创建时指定的选项。

包结构选项的不同值时，会出现此警告 ([/Zp](../../build/reference/zp-struct-member-alignment.md)) 的预编译标头在编译期间指定。