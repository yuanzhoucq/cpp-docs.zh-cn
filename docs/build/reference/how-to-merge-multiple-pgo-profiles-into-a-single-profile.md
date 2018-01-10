---
title: "如何： 将多个 PGO 配置文件合并成单个配置文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 880e9fbba7852a9a7919e73f80b73e34394cd037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：将多个 PGO 配置文件合并成一个配置文件
按配置优化 (PGO) 是一个用于创建优化的二进制文件根据分析的方案的极佳工具。 但如果你有一个应用程序具有几个重要，但又不同方案;如何从多种不同方案创建一个配置文件，可以使用 PGO？ 在 Visual Studio 中，PGO 管理器中，Pgomgr.exe，为你进行此作业。  
  
 合并配置文件的语法是：  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 其中`num`是要用于此合并的可选权重。 如果有更重要比其他一些方案或将要运行多次的情况下，通常使用权重。  
  
> [!NOTE]
>  PGO 管理器不会使用陈旧的配置文件数据。 若要合并到.pgd 文件对应的.pgc 文件，必须由可执行文件，这由生成.pgd 文件的相同链接调用生成的.pgc 文件。  
  
## <a name="example"></a>示例  
 在此示例中，PGO Manager 将添加 pgcFile.pgc pgdFile.pgd 六倍。  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>示例  
 在此示例中，PGO 管理器将 pgcFile1.pgc 和添加 pgcFile2.pgc 到 pgdFile.pgd，两次为每个对应的.pgc 文件。  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>示例  
 如果没有对应的.pgc 文件的情况下运行 PGO 管理器，则编译器将搜索为带有叹号 （！） 跟任意字符追加.pgd 文件具有相同名称的所有对应的.pgc 文件的本地目录。 如果本地目录具有文件 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，和从本地目录运行以下命令，然后 test!1.pgc 和 test!hello.pgc 将合并到 test.pgd。  
  
```  
pgomgr /merge test.pgd  
```  
  
## <a name="see-also"></a>请参阅  
 [按配置文件优化](../../build/reference/profile-guided-optimizations.md)