---
title: 计算所需值 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8f51e448aab0978d6a7eb39a753c2274d2cae6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369323"
---
# <a name="calculating-necessary-values"></a>计算所需值
两条关键信息需要通过延迟 helper 例程。 为此，用于计算此信息的 delayhlp.cpp 中有两个内联函数。  
  
-   第一个计算当前导入 （导入地址表 (IAT)、 绑定导入地址表 (BIAT) 和未绑定导入地址表 (UIAT)） 在三个不同的表的索引。  
  
-   第二个计算有效 IAT 中导入的数量。  
  
```  
// utility function for calculating the index of the current import  
// for all the tables (INT, BIAT, UIAT, and IAT).  
__inline unsigned  
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {  
    return pitdCur - pitdBase;  
    }  
  
// utility function for calculating the count of imports given the base  
// of the IAT. NB: this only works on a valid IAT!  
__inline unsigned  
CountOfImports(PCImgThunkData pitdBase) {  
    unsigned        cRet = 0;  
    PCImgThunkData  pitd = pitdBase;  
    while (pitd->u1.Function) {  
        pitd++;  
        cRet++;  
        }  
    return cRet;  
    }  
```  
  
## <a name="see-also"></a>请参阅  
 [了解 Helper 函数](understanding-the-helper-function.md)