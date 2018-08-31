---
title: 编译器警告 （等级 1） C4952 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62f4c18380d89eb516a5fa49ef63e92ab79a6f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207146"
---
# <a name="compiler-warning-level-1-c4952"></a>编译器警告（等级 1）C4952

> '*函数*： 在程序数据库中找到的任何配置文件数据'*pgd_file*

使用时[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到之后重新编译输入的模块`/LTCG:PGINSTRUMENT`并且有一个新函数 (*函数*) 存在。

此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。