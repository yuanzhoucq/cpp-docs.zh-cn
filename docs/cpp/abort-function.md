---
title: abort 函数
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451228"
---
# <a name="abort-function"></a>abort 函数

**中止**函数，同样在标准包含文件中声明\<stdlib.h >，将终止 C++ 程序。 之间的差异`exit`并**中止**在于`exit`可用于 c + + 运行时终止处理，才能开始 （全局对象将调用析构函数），而**中止**立即终止程序。 有关详细信息，请参阅[中止](../c-runtime-library/reference/abort.md)中*运行时库参考*。

## <a name="see-also"></a>请参阅

[程序终止](../cpp/program-termination.md)