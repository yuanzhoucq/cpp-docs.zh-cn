---
title: 使用导入库和导出文件
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: 71162d896ee76d99f5d47dfa670b62d456243837
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445677"
---
# <a name="working-with-import-libraries-and-export-files"></a>使用导入库和导出文件

可以使用 /DEF 选项使用 LIB 创建的导入库和导出文件。 导出文件生成包含的程序的链接使用导出 （通常动态链接库 (DLL)） 并使用导入库来解析引用其他程序中对这些导出。

请注意，是否创建.dll 之前，可以在初始步骤中，创建导入库，则必须通过同一组对象文件时生成.dll 文件，为通过生成导入库时。

在大多数情况下，不需要使用 LIB 创建导入库。 当链接包含导出的程序 （可执行文件或 DLL） 时，链接将自动创建描述导出的导入库。 更高版本，链接时引用这些导出的程序，您指定的导入库。

但是时 DLL 将导出到一个程序，它还中导入，, 是否直接或间接地，您必须使用 LIB 创建的导入库之一。 当 LIB 创建的导入库时，它还会创建一个导出文件。 链接的一个 Dll 时，必须使用导出文件。

## <a name="see-also"></a>请参阅

[LIB 引用](../../build/reference/lib-reference.md)