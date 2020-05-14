---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295226"
---
# <a name="pgomgr"></a>pgomgr

将配置文件数据从一个或多个 .pgc 文件到 .pgd 文件。

## <a name="syntax"></a>语法

> pgomgr  [options  ] pgcfiles  pgdfile 

### <a name="parameters"></a>参数

*options*<br/>
可以对 pgomgr  指定以下选项：

-  或   显示可用 pgomgr  选项。

- /clear  导致从 .pgd 文件中清除所有配置文件信息。 指定 /clear  时，无法指定 .pgc 文件。

- /detail  显示详细统计信息，包括流图形覆盖信息。

- /summary  显示每个函数的统计信息。

- /unique  与 /summary  一起使用时，会导致显示修饰的函数名称。 默认情况下，未使用 /unique  时，表示要显示未修饰的函数名称。

- /merge  \[:  <em>n</em>] 导致 .pgc 文件中的数据添加到 .pgd 文件中。 可选参数 n  可让你指定应添加 n  次数据。 例如，如果某个方案通常会执行六次以反映客户执行的频率，则可以在测试运行中执行一次，然后使用 pgomgr /merge:6  将它添加到 .pgd 文件中六次。

pgcfiles <br/>
其配置文件数据要合并到 .pgd 文件中的一个或多个 .pgc 文件。 可以指定单个 .pgc 文件或多个 .pgc 文件。 如果未指定任何 .pgc 文件，则 pgomgr  会合并其文件名与 .pgd 文件相同的所有 .pgc 文件。

pgdfile <br/>
要将 .pgc 文件中的数据合并到其中的 .pgd 文件。

## <a name="remarks"></a>备注

> [!NOTE]
> 只能从 Visual Studio 开发人员命令提示启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

## <a name="example"></a>示例

此示例命令将清除 myapp.pgd 文件中的配置文件数据：

`pgomgr /clear myapp.pgd`

此示例命令将 myapp1.pgc 中的配置文件数据添加到 .pgd 文件三次：

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

在此示例中，将所有 myapp#.pgc 文件中的配置文件数据添加到 myapp.pgd 文件中。

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>请参阅

[按配置优化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
