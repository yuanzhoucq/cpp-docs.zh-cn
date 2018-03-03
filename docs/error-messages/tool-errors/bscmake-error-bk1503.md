---
title: "BSCMAKE 错误 BK1503 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86f2b6d282857409cdb1e1d49e04775e9886cde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 错误 BK1503
无法写入文件 filename [: 原因]  
  
 BSCMAKE 将合并到一个浏览器数据库的编译过程生成的.sbr 文件。 如果生成的浏览器数据库超过 64 MB，或输入 (.sbr) 文件数超过 4092，将发出此错误。  
  
 如果问题由多个 4092.sbr 文件，则必须减小输入文件的数目。 从 Visual Studio 中，这可以通过实现[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)整个项目，然后重新检查基于文件的文件。  
  
 如果问题引起大于 64 MB 的.bsc 文件，则减小作为输入的.sbr 文件数目将减少生成的.bsc 文件的大小。 此外，通过使用 /Em （排除宏展开符号）、 /El （排除本地变量） 和 /Es （排除系统文件） 可能会降低浏览信息的量。  
  
## <a name="see-also"></a>请参阅  
 [BSCMAKE 选项](../../build/reference/bscmake-options.md)