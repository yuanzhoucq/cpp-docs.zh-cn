---
title: 计算所需值
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426403"
---
# <a name="calculating-necessary-values"></a>计算所需值

需要通过延迟帮助器例程来计算两个关键信息。 为此，用于计算此信息 delayhlp.cpp 中有两个内联函数。

- 第一个计算当前导入 （导入地址表 (IAT)、 绑定导入地址表 (BIAT) 和未绑定导入地址表 (UIAT)） 在三个不同的表的索引。

- 第二个中有效 IAT 的导入的计数。

```cpp
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
