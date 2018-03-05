---
title: "使用导入库和导出文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0d60eed00abc60c09e03838a113c424d8f173a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-import-libraries-and-export-files"></a>使用导入库和导出文件
你可以使用 LIB /DEF 选项创建导入库和导出文件。 要生成一个包含的程序导出文件的链接使用导出 （通常动态链接库 (DLL)），并使用导入库解析其他程序中对这些导出的引用。  
  
 请注意，是否创建.dll 之前，可以在初步步骤中，创建你导入的库，你必须传递同一套对象文件时，生成.dll 为通过生成导入库时。  
  
 在大多数情况下，你不需要使用 LIB 创建你导入的库。 当链接包含导出的程序 （可执行文件或 DLL） 时，链接将自动创建描述导出导入库。 更高版本，链接时引用这些导出的程序，你指定的导入库。  
  
 但是时 DLL 将导出到它也从中导入的程序，, 是否直接或间接，你必须使用 LIB 创建导入库之一。 当 LIB 创建导入库时，它还会创建一个导出文件。 链接的一个 Dll 时，必须使用导出文件。  
  
## <a name="see-also"></a>请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)