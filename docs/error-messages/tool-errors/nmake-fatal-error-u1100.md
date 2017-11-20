---
title: "NMAKE 错误 U1100 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1100
dev_langs: C++
helpviewer_keywords: U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b489c1276b62e28fd540df369a84835c98da87e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100
宏 macroname 是非法的批处理规则 rule 的上下文中  
  
 当批模式规则的命令块直接或间接地引用非 $< 的特殊文件宏时，NMAKE 生成该错误。  
  
 $< 是批模式规则唯一可以使用的宏。