---
title: 在预处理中执行程序
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: 564e4aebb3a0502f18550fb9d323e8b30f1303f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271588"
---
# <a name="executing-a-program-in-preprocessing"></a>在预处理中执行程序

若要在预处理期间使用命令的退出代码，请用方括号 ([]) 内的任意参数指定命令。 任何宏被展开前执行此命令。 NMAKE 替换该命令的退出代码，可以在表达式中使用来控制预处理命令规范。

## <a name="see-also"></a>请参阅

[生成文件预处理中的表达式](expressions-in-makefile-preprocessing.md)
