---
title: ".Exp 文件作为链接器输入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5cd6351623b230e3be1e432bd6ee0fb760da5abd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exp-files-as-linker-input"></a>用作链接器输入的 .Exp 文件
导出 (.exp) 文件包含导出的函数和数据项目的信息。 当 LIB 创建导入库时，它还创建了.exp 文件。 当你将同时导出文件，直接或间接从另一个程序导入的程序时，你可以使用.exp 文件。 如果使用了.exp 文件进行链接，链接将不生成导入库，，因为它假定 LIB 已创建一个。 有关.exp 文件和导入库的详细信息，请参阅[使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)。  
  
## <a name="see-also"></a>请参阅  
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)