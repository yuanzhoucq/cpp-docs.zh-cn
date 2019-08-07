---
title: 在 Windows 上运行 Linux 程序
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 6b59d7685aaada3ba44c03da2e5c27c75c8a473a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682389"
---
# <a name="running-linux-programs-on-windows"></a>在 Windows 上运行 Linux 程序

要在 Windows 上运行 Linux 程序，可以使用以下选项：

- 在适用于 Linux (WSL) 的 Windows 子系统上按原样运行程序。 在 WSL 中，程序直接在计算机硬件上执行，而不是在虚拟机中执行。 WSL 还支持 Windows 和 Linux 系统之间的直接文件系统调用，无需 SSL 传输。 WSL 设计为命令行环境，不建议用于图形密集型应用程序。 有关详细信息，请参阅[适用于 Linux 的 Windows 子系统文档](/windows/wsl/about)。
- 在本地计算机或 Azure 上，在 Linux 虚拟机或 Docker 容器中运行程序。 有关详细信息，请参阅[虚拟机](https://azure.microsoft.com/services/virtual-machines/)和[ Azure 上的 Docker](https://docs.microsoft.com/azure/docker/)。
- 在 [MinGW](http://MinGW.org/) 或 [MinGW-w64](https://MinGW-w64.org/doku.php) 环境（这些环境提供从 Linux 到 Windows 系统调用的转换层）中使用 gcc 或 clang 编译程序。
- 在 [Cygwin](https://www.cygwin.com/) 环境（该环境提供在 Windows 上比 MinGW 或 MinGW-w64 更完整的 Linux 环境）中使用 gcc 或 clang 编译和运行程序。
- 从 Linux 手动移植代码，并使用 Microsoft C++ (MSVC) 为 Windows 进行编译。 这涉及将独立于平台的代码重构为单独的库，然后重新编写特定于 Linux 的代码以使用特定于 Windows 的代码（例如 Win32 或 DirectX API）。 对于需要高性能图形的应用程序，这可能是最佳方式。

