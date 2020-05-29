---
title: 重新分发 Visual C++ ActiveX 控件
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4c7806502024789ed41f3043d7db6c87c7c71ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359881"
---
# <a name="redistributing-visual-c-activex-controls"></a>重新分发 Visual C++ ActiveX 控件

Visual C++ 6.0 提供 ActiveX 控件，供你在应用程序中使用并且随后重新分发。 这些控件不再包含在 Visual C++ 中。 根据 Visual C++ 6.0 许可协议，可以使用在 Visual C++ 中开发的应用程序重新分发这些控件。

> [!NOTE]
> Microsoft 不再支持 Visual C++ 6.0。

有关可再发行的 Visual C++ 6.0 ActiveX 控件列表，请参阅 Visual C++ 6.0 产品 CD 光盘 1 上的 Common\Redist\Redist.txt。

分发应用程序时，必须安装并注册 ActiveX 控件的 .ocx（使用 Regsvr32.exe）。 此外，应确保目标计算机具有以下系统文件的当前版本（星号指示文件需要注册）：

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

如果这些 DLL 不适用于目标系统，则需要使用更新相应操作系统所规定的机制更新 DLL。 可以从 下载 Windows 操作系统的最新服务包[http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com)。

使用连接到数据库的 ActiveX 控件时，还需要在目标计算机上复制数据源名称。 可以用函数（如 `ConfigDSN`）以编程方式来完成此操作。

某些可再发行的 ActiveX 控件具有其他依赖项。 对于 Visual C++ 6.0 产品 CD 上的 Os\System 文件夹中的每个 .ocx 文件，还有 .dep 文件。 对于想要重新分发的每个 .ocx 文件，请在相应的 .dep 文件中寻找一个或多个 USES 项。 如果已列出文件，则必须确保该文件位于目标计算机上。 直接支持 .ocx 文件的任何 DLL 都需要注册。 （要使 Regsvr32.exe 成功，目标计算机必须首先包含控件静态加载的所有 DLL。此外，如果列为依赖项的 DLL 在 Visual C++ 6.0 CD 上的 Os_System 文件夹中也有 .dep 文件，则还必须调查该 .dep 文件以用于 USES 条目。

## <a name="see-also"></a>另请参阅

[重新分发 Visual C++ 文件](redistributing-visual-cpp-files.md)
