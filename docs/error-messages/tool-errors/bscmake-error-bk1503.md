---
title: BSCMAKE 错误 BK1503 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1503
dev_langs:
- C++
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06d4a05a8f2d04c3f8a991d4444b35295408a7b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294789"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE 错误 BK1503
无法写入文件 filename [: 原因]  
  
 BSCMAKE 将合并到一个浏览器数据库的编译过程生成的.sbr 文件。 如果生成的浏览器数据库超过 64 MB，或输入 (.sbr) 文件数超过 4092，将发出此错误。  
  
 如果问题由多个 4092.sbr 文件，则必须减小输入文件的数目。 从 Visual Studio 中，这可以通过实现[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)整个项目，然后重新检查基于文件的文件。  
  
 如果问题引起大于 64 MB 的.bsc 文件，则减小作为输入的.sbr 文件数目将减少生成的.bsc 文件的大小。 此外，通过使用 /Em （排除宏展开符号）、 /El （排除本地变量） 和 /Es （排除系统文件） 可能会降低浏览信息的量。  
  
## <a name="see-also"></a>请参阅  
 [BSCMAKE 选项](../../build/reference/bscmake-options.md)