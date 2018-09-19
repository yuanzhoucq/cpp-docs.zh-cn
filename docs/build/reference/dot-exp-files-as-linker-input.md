---
title: .用作链接器输入的 exp 文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4badc93f38d5ce76dcc294ad4ae216c8e3f6454c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724004"
---
# <a name="exp-files-as-linker-input"></a>用作链接器输入的 .Exp 文件

导出 (.exp) 文件包含有关导出的函数和数据项目的信息。 当 LIB 创建的导入库时，它还创建了.exp 文件。 链接都将导出到并直接或间接从另一个程序导入的程序时使用.exp 文件。 如果使用了.exp 文件链接，链接不生成导入库，因为它假定 LIB 已创建一个。 .Exp 文件和导入库有关的详细信息，请参阅[使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)。

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)<br/>
[链接器选项](../../build/reference/linker-options.md)