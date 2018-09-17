---
title: 使用导入库和导出文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28b4b94025c813ea526964ed6395a2e6af1ac0b9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721235"
---
# <a name="working-with-import-libraries-and-export-files"></a>使用导入库和导出文件

可以使用 /DEF 选项使用 LIB 创建的导入库和导出文件。 导出文件生成包含的程序的链接使用导出 （通常动态链接库 (DLL)） 并使用导入库来解析引用其他程序中对这些导出。

请注意，是否创建.dll 之前，可以在初始步骤中，创建导入库，则必须通过同一组对象文件时生成.dll 文件，为通过生成导入库时。

在大多数情况下，不需要使用 LIB 创建导入库。 当链接包含导出的程序 （可执行文件或 DLL） 时，链接将自动创建描述导出的导入库。 更高版本，链接时引用这些导出的程序，您指定的导入库。

但是时 DLL 将导出到一个程序，它还中导入，, 是否直接或间接地，您必须使用 LIB 创建的导入库之一。 当 LIB 创建的导入库时，它还会创建一个导出文件。 链接的一个 Dll 时，必须使用导出文件。

## <a name="see-also"></a>请参阅

[LIB 引用](../../build/reference/lib-reference.md)