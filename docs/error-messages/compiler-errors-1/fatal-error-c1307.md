---
title: "错误 C1307 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1173f538f02e8178d523bb51476b4a10427099ea
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1307"></a>错误 C1307
自收集配置文件数据后已编辑了程序  
  
 使用时[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 链接器检测到 /ltcg: pginstrument 后已重新编译输入的模块和模块已更改为其中现有配置文件数据已不再相关的点。 例如，如果在重新编译的模块中更改的调用关系图，编译器将生成 C1307。  
  
 若要解决此错误，运行 /ltcg: pginstrument、 重做所有测试运行，并运行 /ltcg: pgoptimize。 如果你不能运行 /ltcg: pginstrument 和重做所有测试运行，使用 /LTCG:PGUPDATE 而不是 /ltcg: pgoptimize 创建优化的映像。
