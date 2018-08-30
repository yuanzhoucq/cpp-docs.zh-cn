---
title: 编译器警告 （等级 1） C4953 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e53808d4ad97bad4eccdf81b0a863277f8f7796
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194627"
---
# <a name="compiler-warning-level-1-c4953"></a>编译器警告（等级 1）C4953

> 被内联方*函数*已编辑过收集配置文件数据后，不使用配置文件数据

使用时[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，编译器检测到之后重新编译输入的模块`/LTCG:PGINSTRUMENT`并且有一个函数 (*函数*) 的编辑和标识现有测试运行函数的候选项作为内联。 但是，重新编译该模块后，此函数不再是内联的候选项。

此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。