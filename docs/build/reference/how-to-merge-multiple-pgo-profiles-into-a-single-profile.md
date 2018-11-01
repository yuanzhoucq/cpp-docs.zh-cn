---
title: 如何：将多个 PGO 配置文件合并成一个配置文件
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 04730524fa756b0c6f1e505f3610609bdec6262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476539"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：将多个 PGO 配置文件合并成一个配置文件

按配置优化 (PGO) 是用于创建优化的二进制文件基于分析的应用场景的出色工具。 但是，如果有具有几个重要的是，但又不同方案的应用程序？ 如何从多种不同方案创建单个配置文件，PGO 可以使用？ 在 Visual Studio 中，PGO 管理器中， [pgomgr.exe](pgomgr.md)，完成此作业。

合并配置文件的语法是：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中`num`是一个可选的权重，用于添加此合并的.pgc 文件。 如果有某些情况下比其他更重要的或将要运行多次的情况下，通常使用权重。

> [!NOTE]
> PGO Manager 并不适用于过时的配置文件数据。 若要合并到一个.pgd 文件的.pgc 文件，必须由可执行文件的已生成了.pgd 文件的同一链接调用通过生成.pgc 文件。

## <a name="examples"></a>示例

在此示例中，PGO Manager 向 pgcFile.pgc pgdFile.pgd 六倍：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此示例中，PGO Manager 向 pgcFile1.pgc 和 pgcFile2.pgc pgdFile.pgd，两次为每个.pgc 文件：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果任何.pgc 文件参数的情况下运行 PGO 管理器时，它将搜索所有具有相同的基名称为后跟一个感叹号 （！），然后一个或多个任意字符的.pgd 文件的.pgc 文件的本地目录。 例如，如果本地目录拥有文件 test.pgd、 test!1.pgc、 test2.pgc 和 test!hello.pgc，但以下命令运行从本地目录中，然后**pgomgr** test!1.pgc 和 test!hello.pgc 合并 test.pgd。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>请参阅

[按配置文件优化](../../build/reference/profile-guided-optimizations.md)
