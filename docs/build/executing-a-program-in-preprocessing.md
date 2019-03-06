---
title: 在预处理中执行程序
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: d95079349981b073533bb00abcd053454542a044
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413298"
---
# <a name="executing-a-program-in-preprocessing"></a>在预处理中执行程序

若要在预处理期间使用命令的退出代码，请用方括号 ([]) 内的任意参数指定命令。 任何宏被展开前执行此命令。 NMAKE 替换该命令的退出代码，可以在表达式中使用来控制预处理命令规范。

## <a name="see-also"></a>请参阅

[生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)
