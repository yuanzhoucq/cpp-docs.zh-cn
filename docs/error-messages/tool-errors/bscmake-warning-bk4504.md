---
title: "BSCMAKE 警告 BK4504 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK4504
dev_langs: C++
helpviewer_keywords: BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 58a59b3141a8d7051aa7ece1bcb71dd960fabb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504
文件包含引用太多;忽略来自此源的更多参考  
  
 .cpp 文件包含 64,000 个以上的符号引用。 当 BSCMAKE 在某个文件中遇到 64,000 个引用之后，它将会忽略所有后续的引用。  
  
 若要更正此问题，请将该文件拆分为两个或更多文件（每个文件包含 64,000 个以下的符号引用），或使用 `#pragma component(browser)` 预处理器指令限制为特定引用生成的符号。 有关详细信息，请参阅[组件](../../preprocessor/component.md)。