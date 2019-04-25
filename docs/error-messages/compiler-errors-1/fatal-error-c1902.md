---
title: 错误 C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165861"
---
# <a name="fatal-error-c1902"></a>错误 C1902

程序数据库管理器不匹配;请检查安装

程序数据库文件 (.pdb) 使用 mspdb 的较新版本创建*XXX*.dll 编译器找到了你的系统。 此错误通常指示缺少 mspdbsrv.exe 或 mspdbcore.dll，或者它们或具有不同版本与 mspdb*XXX*.dll。 ( *XXX* mspdb 占位符*XXX*随每个产品版本的.dll 文件名称更改。 例如，在 Visual Studio 2015 中，文件名为 mspdb140.dll。）

确保匹配版本的 mspdbsrv.exe、 mspdbcore.dll 和 mspdb*XXX*你系统上安装.dll。 请确保不复制不匹配的版本为包含您的目标平台的编译器和链接工具的目录。 例如，您可能已经复制文件以便您可以调用该编译器或链接的工具，在命令提示符下设置不**路径**环境变量相应地。