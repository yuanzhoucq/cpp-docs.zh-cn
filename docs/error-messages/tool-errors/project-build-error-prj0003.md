---
title: 项目生成错误 PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192921"
---
# <a name="project-build-error-prj0003"></a>项目生成错误 PRJ0003

> 生成 "*命令行*" 时出错。

"**属性页**" 对话框中的 "输入" 生成的*命令行*命令返回了错误代码，但在 "**输出**" 窗口中没有显示信息。

此错误的可能原因包括：

- 你的项目依赖于 ATL 服务器。 从 Visual Studio 2008 开始，ATL Server 不再作为 Visual Studio 的一部分提供，而是在 CodePlex 中作为共享源项目发布。 若要下载 ATL 服务器源代码和工具，请参阅[Atl 服务器库和工具](https://go.microsoft.com/fwlink/p/?linkid=81979)。

- 系统资源不足。 关闭一些应用程序以解决此问题。

- 安全权限不足。 验证你是否具有足够的安全特权。

- 在**VC + + 目录**中指定的可执行路径不包括您尝试运行的工具的路径。 有关信息，请参阅[设置编译器和生成属性](../../build/working-with-project-properties.md)

- 对于生成文件项目，缺少在**生成命令行**或**重新生成命令行**上运行的命令。

## <a name="see-also"></a>另请参阅

[项目生成错误和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
