---
title: "链接器工具错误 LNK1264 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f590de75998becb9c03c73ac3083b04445a02156
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1264"></a>链接器工具错误 LNK1264
指定的 /ltcg: pginstrument 但不需要; 的代码生成检测失败  
  
 **/Ltcg: pginstrument**已指定，但没有使用已编译的.obj 上未找到文件[/GL](../../build/reference/gl-whole-program-optimization.md)。 检测不能将位置和链接失败。 必须在命令行上至少一个使用编译的.obj 文件**/GL** ，以便检测才能发生。  
  
 按配置优化 (PGO) 选项仅适用于 64 位编译器。