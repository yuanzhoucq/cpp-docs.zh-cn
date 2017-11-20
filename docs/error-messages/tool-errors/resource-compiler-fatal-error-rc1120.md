---
title: "资源编译器错误 RC1120 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1120
dev_langs: C++
helpviewer_keywords: RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9cc1006dad4b0427a4254f4798b206d975e89e03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rc1120"></a>资源编译器错误 RC1120
内存不足，所需的字节数  
  
 资源编译器用尽了将存储在其堆中的项的存储。 通常，这是使过多符号的结果。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 帮助中的虚拟内存。  
  
2.  消除不需要包括文件，尤其是不需要`#define`s 和函数原型。  
  
3.  将当前文件拆分为两个或多个文件，然后单独对其进行编译。  
  
4.  删除其他程序或驱动程序运行在系统中，这可能正在消耗大量的内存。