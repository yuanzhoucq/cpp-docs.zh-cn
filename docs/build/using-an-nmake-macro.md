---
title: "使用 NMAKE 宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9893e7ec1ba29b4b5ed2ccb569a135f44b2ed47f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="using-an-nmake-macro"></a>使用 NMAKE 宏
若要使用宏，请用括号，如下所示前面美元符号 （$） 括起来其名称。  
  
## <a name="syntax"></a>语法  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>备注  
 不允许有空格。 括号是可选的如果*macroname*是单个字符。 定义字符串替换 $(*macroname*); 未定义的宏替换为一个空字符串。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [宏替换](../build/macro-substitution.md)  
  
## <a name="see-also"></a>另请参阅  
 [宏和 NMAKE](../build/macros-and-nmake.md)