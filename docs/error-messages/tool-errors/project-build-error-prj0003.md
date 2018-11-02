---
title: 项目生成错误 PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 9a116f41efc791ed90fbac8065bc339172c9ea9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572376"
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