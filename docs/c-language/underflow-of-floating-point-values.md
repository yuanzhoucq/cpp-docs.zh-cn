---
title: "浮点值的下溢 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f74624f935c9a1384c1c4992004b12c7847e9fd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="underflow-of-floating-point-values"></a>浮点值的下溢
**ANSI 4.5.1** 对于下溢范围错误，数学函数是否将整数表达式 `errno` 设置为宏 `ERANGE` 的值  
  
 浮点下溢不会将表达式 `errno` 设置为 `ERANGE`。 当值接近零且最终下溢时，该值将设置为零。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)