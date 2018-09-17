---
title: 在预处理中执行程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2b0571e67e7c5d24cf31dce6fce548735cad966
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721456"
---
# <a name="executing-a-program-in-preprocessing"></a>在预处理中执行程序

若要在预处理期间使用命令的退出代码，请用方括号 ([]) 内的任意参数指定命令。 任何宏被展开前执行此命令。 NMAKE 替换该命令的退出代码，可以在表达式中使用来控制预处理命令规范。

## <a name="see-also"></a>请参阅

[生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)