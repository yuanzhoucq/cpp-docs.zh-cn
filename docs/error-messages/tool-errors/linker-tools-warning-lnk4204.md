---
title: "链接器工具警告 LNK4204 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f9b2d9611192fe4afe01d178ac3af5fcc8ccc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4204"></a>链接器工具警告 LNK4204
filename 缺少的调试信息引用模块中;正在链接对象，如同没有调试信息  
  
 .Pdb 文件具有错误的签名。 链接器将继续链接没有调试信息的对象。 你可能想要重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项。  
  
 如果某些库中的对象引用不再存在的文件，则会发生 LNK4204。 这可能会发生时重新生成解决方案，例如;对象文件可能会删除并不会重新生成由于编译错误。 在这种情况下，与编译**/Z7**，或**/Fd**，若要更新的对象来引用单个文件每个库 （不是默认.pdb 文件名称）。  有关详细信息，请参阅 [/Fd（程序数据库文件名）](../../build/reference/fd-program-database-file-name.md)。  确保，在每次更新中的源控制系统时，它与以下库保存.pdb。