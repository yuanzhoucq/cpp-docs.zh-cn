---
title: "Null 和未定义宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9581b152057655c510f1cbcd4ab29ba8339070b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="null-and-undefined-macros"></a>null 宏和未定义的宏
Null 和未定义宏会扩展为空字符串，但定义为空字符串的宏被视为预处理表达式中定义。 若要定义为空字符串的宏，请指定任何字符后的命令行或命令文件中的等号 （=） 除外空格或制表符，并将空字符串或定义括在双引号 ("")。 若要取消定义宏，请使用**！UNDEF。** 有关详细信息，请参阅[生成文件预处理指令](../build/makefile-preprocessing-directives.md)。  
  
## <a name="see-also"></a>请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)