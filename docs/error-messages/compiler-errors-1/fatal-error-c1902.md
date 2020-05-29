---
title: 错误 C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: 10a411dfc942498a98959d9a23cb42dfb93cf2ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202821"
---
# <a name="fatal-error-c1902"></a>错误 C1902

程序数据库管理器不匹配;请检查您的安装

使用比编译器在系统中找到*的 mspdb 的*较新版本创建的程序数据库文件（.pdb）。 此错误通常表示缺少 mspdbsrv.exe 或 mspdbcore.dll，或者其版本不同于 mspdb*XXX*。 （Mspdb 中的*xxx*占位符在每个产品版本中都会发生*更改。* 例如，在 Visual Studio 2015 中，文件名为 mspdb140.dll。）

确保在您的系统上安装了 mspdbsrv.exe、mspdbcore.dll*和 mspdb 的匹配版本。* 确保未将不匹配的版本复制到包含编译器和目标平台的链接工具的目录。 例如，你可能已复制了文件，因此可以从命令提示符调用编译器或链接工具，而无需相应地设置**PATH**环境变量。
