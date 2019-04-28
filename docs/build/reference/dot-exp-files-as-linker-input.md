---
title: 用作链接器输入的 .Exp 文件
ms.date: 11/04/2016
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
ms.openlocfilehash: 0f2f5c22752d6d938700228fc208c21b8f32cc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293662"
---
# <a name="exp-files-as-linker-input"></a>用作链接器输入的 .Exp 文件

导出 (.exp) 文件包含有关导出的函数和数据项目的信息。 当 LIB 创建的导入库时，它还创建了.exp 文件。 链接都将导出到并直接或间接从另一个程序导入的程序时使用.exp 文件。 如果使用了.exp 文件链接，链接不生成导入库，因为它假定 LIB 已创建一个。 .Exp 文件和导入库有关的详细信息，请参阅[使用导入库和导出文件](working-with-import-libraries-and-export-files.md)。

## <a name="see-also"></a>请参阅

[LINK 输入文件](link-input-files.md)<br/>
[MSVC 链接器选项](linker-options.md)
