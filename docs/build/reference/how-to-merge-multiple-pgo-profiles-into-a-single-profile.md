---
title: 如何： 将多个 PGO 配置文件合并成单个配置文件 |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 450aa6c763c44176ce6cb03313abcb419dc7315c
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：将多个 PGO 配置文件合并成一个配置文件

按配置优化 (PGO) 是一个用于创建优化的二进制文件根据分析的方案的极佳工具。 但是，如果有具有几个重要，但又不同方案的应用程序？ 如何从多种不同方案创建一个配置文件，可以使用 PGO？ 在 Visual Studio 中，PGO 管理器中， [pgomgr.exe](pgomgr.md)，会为您完成此作业。

合并配置文件的语法是：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中`num`是要用于添加通过此合并的.pgc 文件的可选权重。 如果有更重要比其他一些方案或将要运行多次的情况下，通常使用权重。

> [!NOTE]
> PGO Manager 并不适用于陈旧的配置文件数据。 若要合并到.pgd 文件对应的.pgc 文件，必须由可执行文件，这由生成.pgd 文件的相同链接调用生成的.pgc 文件。

## <a name="examples"></a>示例

在此示例中，PGO Manager 向 pgcFile.pgc pgdFile.pgd 六倍：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此示例中，PGO 管理器将 pgcFile1.pgc 和 pgcFile2.pgc 添加到 pgdFile.pgd，两次为每个对应的.pgc 文件：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果不使用任何对应的.pgc 文件参数运行的 PGO 管理器，它将搜索与跟叹号 （！），然后一个或多个任意字符的.pgd 文件具有相同的基名称的所有对应的.pgc 文件的本地目录。 例如，如果本地目录文件 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，并且初始屏幕然后从本地目录中，运行以下命令，是**pgomgr**将 test!1.pgc 和 test!hello.pgc 合并到 test.pgd。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>请参阅

[按配置文件优化](../../build/reference/profile-guided-optimizations.md)
