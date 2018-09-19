---
title: 项目生成错误 PRJ0003 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d1a23b8171c916b05df1d715f803893ab0720e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053812"
---
# <a name="project-build-error-prj0003"></a>项目生成错误 PRJ0003

> 错误生成 '*命令行*。

*命令行*命令中的输入来形成**属性页**对话框的返回错误代码，但没有信息会显示在**输出**窗口。

此错误的可能原因包括：

- 你的项目依赖于 ATL 服务器。 从 Visual Studio 2008 开始，ATL Server 不再包含在 Visual Studio 中，但已作为 CodePlex 上的共享源项目发布。 若要下载 ATL Server 源代码和工具，请转到[ATL 服务器库和工具](http://go.microsoft.com/fwlink/p/?linkid=81979)。

- 较低的系统资源。 关闭一些应用程序以解决此问题。

- 没有足够的安全特权。 验证具有足够的安全特权。

- 中指定的可执行文件路径**VC + + 目录**不包括尝试运行该工具的路径。 有关信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)

- 对生成文件项目缺少一个用于在运行命令**生成命令行**或**重新生成命令行**。

## <a name="see-also"></a>请参阅

[项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)