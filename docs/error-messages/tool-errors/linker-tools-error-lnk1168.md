---
title: 链接器工具错误 LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: f0eb63c124162dbb515782bbd014c556c12de153
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450888"
---
# <a name="linker-tools-error-lnk1168"></a>链接器工具错误 LNK1168

无法打开 filename 进行写入

链接器无法写入 `filename`。 文件可能正在使用中且其文件句柄已被其他进程锁定，或者你可能没有对该文件或者对其所在的目录或网络共享的写入权限。 此错误通常由暂时情况引起，例如，防病毒程序持有的锁文件搜索索引进程，或由 Visual Studio 生成系统持有中释放锁的延迟。

若要修复此问题，请验证 `filename` 文件句柄是否锁定以及你是否具有对此文件的写入权限。 如果它是可执行文件，则请验证它是否已在运行。

可以使用 Windows SysInternals 实用工具[处理](/sysinternals/downloads/handle)或[Process Explorer](/sysinternals/downloads/process-explorer)若要确定哪个进程具有的文件句柄上的锁`filename`。 你还可以使用进程资源管理器释放开放式文件句柄上的锁。 有关如何使用这些实用工具的信息，请参阅它们附带的帮助文件。

如果文件被防病毒程序锁定，则可以通过防病毒程序从自动扫描中排除生成输出目录，从而修复此问题。 防病毒扫描程序通常当在文件系统中创建新文件时触发，在扫描继续时，它们持有文件上的锁。 有关如何从扫描中排除特定目录的详细信息，请参考防病毒程序文档。

如果文件被搜索索引服务锁定，则可通过从自动索引中排除生成输出目录来修复此问题。 有关详细信息，请参考索引服务的文档。 若要更改 Windows 搜索索引服务，请使用**索引选项**在 Windows 中**控制面板**。 有关详细信息，请参阅[搜索 Windows 10 中的索引：常见问题解答](https://support.microsoft.com/help/4098843/windows-10-search-indexing-faq)。

如果可执行文件无法被生成进程覆盖，则可能被文件资源管理器锁定。 如果**应用程序体验**服务已被禁用，文件资源管理器可能保持的可执行文件句柄锁长一段时间。 若要解决此问题，请运行**services.msc** ，然后打开**属性**对话框**应用程序体验**服务。 更改**启动类型**从**禁用**到**手动**。
