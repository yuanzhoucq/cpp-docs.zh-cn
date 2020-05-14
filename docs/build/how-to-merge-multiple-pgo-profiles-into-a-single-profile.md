---
title: 如何：将多个 PGO 配置文件合并成一个配置文件
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188868"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>如何：将多个 PGO 配置文件合并成一个配置文件

按配置优化 (PGO) 是基于已分析的创建创建优化二进制文件的绝佳工具。 但如果你的应用程序有几个重要但不同的使用场景，该怎么办？ 如何创建可供 PGO 用于多种不同方案的单一配置文件？ 在 Visual Studio 中，PGO Manager [pgomgr.exe](pgomgr.md) 可为你执行此操作。

合并配置文件的语法是：

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

其中 `num` 是可用于此合并添加的 .pgc 文件的可选权重。 如果某些方案比其他方案更重要，或者在某些情况下需要多次运行，则通常使用权重。

> [!NOTE]
> PGO Manager 不适用于过时的配置文件数据。 要将 .pgc 文件合并到 .pgd 文件中，.pgc 文件必须由生成 .pgd 文件的同一链接调用创建的可执行文件生成。

## <a name="examples"></a>示例

在此示例中，PGO Manager 将 pgcFile.pgc 添加到 pgdFile.pgd 六次：

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

在此示例中，PGO Manager 将 pgcFile1.pgc 和 pgcFile2.pgc 添加到 pgdFile.pgd，每个 .pgc 文件添加两次：

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

如果 PGO Manager 运行时没有任何 .pgc 文件参数，它将搜索本地目录中所有与感叹号 (!) 后面的 .pgd 文件具有相同基名的所有 .pgc 文件，然后搜索一个或多个任意字符。 例如，如果本地目录包含 test.pgd、test!1.pgc、test2.pgc 和 test!hello.pgc 文件，并且从本地目录运行以下命令，则 pgomgr 会将 test!1.pgc 和 test!hello.pgc 合并到 test.pgd  。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>请参阅

[按配置优化](profile-guided-optimizations.md)
