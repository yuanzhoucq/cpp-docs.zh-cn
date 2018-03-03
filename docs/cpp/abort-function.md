---
title: "abort 函数 |Microsoft 文档"
ms.custom: 
ms.date: 12/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73c2549e5ce29823376b378b9dc565e2d883ffa
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="abort-function"></a>abort 函数

**中止**函数，同样在标准包含文件中声明\<stdlib.h >，将终止 c + + 程序。 之间的差异**退出**和**中止**在于**退出**允许执行 c + + 运行时终止处理 （全局对象将调用析构函数），而**中止**立即终止程序。 有关详细信息，请参阅[中止](../c-runtime-library/reference/abort.md)中*运行时库参考*。

## <a name="see-also"></a>请参阅

[程序终止](../cpp/program-termination.md)