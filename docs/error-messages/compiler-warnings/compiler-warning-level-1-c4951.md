---
title: 编译器警告 （等级 1） C4951 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204230"
---
# <a name="compiler-warning-level-1-c4951"></a>编译器警告（等级 1）C4951

> '*函数*已编辑过收集配置文件数据后，没有使用函数配置文件数据

在输入模块中已将函数编辑为 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此配置文件数据现在无效。 输入的模块后已重新编译 **/ltcg: pginstrument**并且有一个函数 (*函数*) 的控件不是模块中的时间不同的流与 **/ltcg: pginstrument**操作。

此警告为信息性。 若要解决此警告，请运行 **/LTCG:PGINSTRUMENT**，重做所有测试，并运行 **/LTCG:PGOPTIMIZE**。

如果已使用 **/LTCG:PGOPTIMIZE** ，此警告将替换为一个错误。