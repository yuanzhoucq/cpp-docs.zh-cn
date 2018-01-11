---
title: "编译器警告 （等级 1） C4951 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4951
dev_langs: C++
helpviewer_keywords: C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 199df135d5d2c00255037e5a1b31db80e2683d4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4951"></a>编译器警告（等级 1）C4951
收集配置文件数据后已编辑过“函数”，没有使用函数配置文件数据  
  
 在输入模块中已将函数编辑为 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此配置文件数据现在无效。 在 **/ltcg: pginstrument** 后已重新编译输入模块并且有一个函数（***函数***），使用的控制流不是在执行 **/ltcg: pginstrument** 操作时模块中的控制流。  
  
 此警告为信息性。 若要解决此警告，请运行 **/LTCG:PGINSTRUMENT**，重做所有测试，并运行 **/LTCG:PGOPTIMIZE**。  
  
 如果已使用 **/LTCG:PGOPTIMIZE** ，此警告将替换为一个错误。