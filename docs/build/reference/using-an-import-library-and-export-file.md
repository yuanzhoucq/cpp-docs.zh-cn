---
title: 使用导入库和导出文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37d77fdc4df7d2e7239b8bba652d8cf8f4bbc997
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-import-library-and-export-file"></a>使用导入库和导出文件
当程序 （可执行文件或 DLL） 将导出到的也是它，从中导入另一个程序，或者如果两个以上程序同时将导出到和从相互导入，链接这些程序的命令必须提供循环导出。  
  
 在没有循环导出的情况，当链接使用的程序的另一个程序中，导出时必须指定导出的程序的导入库。 导出程序的导入库链接该导出程序时创建。 因此，你必须链接导出程序之前导入程序。 例如，如果 TWO.dll 导入从 ONE.dll，你必须首先将链接 ONE.dll 并获取导入库 ONE.lib。 然后，链接 TWO.dll 时指定 ONE.lib。 时链接器将创建 TWO.dll，它还会创建其导入库，TWO.lib。 链接从 TWO.dll 导入的程序时，请使用 TWO.lib。  
  
 但是，在循环导出情况下，不能链接所有相互依赖的程序使用其他程序的导入库。 在前面所述，如果 TWO.dll 还将导出到 ONE.dll，不会存在 TWO.dll 导入库时链接 ONE.dll 示例。 循环导出当存在时，必须使用 LIB 创建导入库和导出程序之一的文件。  
  
 若要开始，可以选择在其上运行 LIB 程序之一。 在 LIB 命令中，列出了所有对象和库的程序，并指定 /def。 如果程序使用.def 文件或 /EXPORT 规范，则也应指定这些信息。  
  
 创建导入库 (.lib) 和程序的导出文件 (.exp) 后，你使用的导入库链接的其他程序时。 链接创建每个导出程序生成导入库。 例如，如果 ONE.dll 上的对象和导出运行 LIB，你创建 ONE.lib 和 ONE.exp。链接 TWO.dll; 时，你现在可以使用 ONE.lib此步骤还创建导入库 TWO.lib。  
  
 最后，链接以开头的程序。 LINK 命令中，在指定的对象和库 LIB 创建程序，和导入库的.exp 文件、 程序所使用的导出的库。 若要继续此示例，ONE.dll 链接命令包含 ONE.exp 和 TWO.lib，以及对象和转到 ONE.dll 的库。 LINK 命令中; 中不能指定.def 文件或 /EXPORT 规范这些不需要，因为.exp 文件中包含的导出定义。 当使用了.exp 文件进行链接时，链接不会创建导入库，创建.exp 文件时，因为它假定一个已创建。  
  
## <a name="see-also"></a>请参阅  
 [使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)