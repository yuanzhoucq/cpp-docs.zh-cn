---
title: 用作链接器输入的 .Res 文件
ms.date: 11/04/2016
helpviewer_keywords:
- RES files as linker input
- .res files as linker input
- linking [C++], resource files
- resource files, linking
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
ms.openlocfilehash: 3cbddba1273d579454560f176df00b09b03c89bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575082"
---
# <a name="res-files-as-linker-input"></a>用作链接器输入的 .Res 文件

链接程序时，可以指定一个.res 文件。 资源编译器 (RC) 创建.res 文件。 链接自动将.res 文件转换到 COFF。 CVTRES.exe 工具必须在 LINK.exe 所在的同一目录中或在 PATH 环境变量中指定的目录中。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)<br/>
[链接器选项](../../build/reference/linker-options.md)