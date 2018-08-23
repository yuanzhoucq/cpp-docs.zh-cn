---
title: 链接器工具错误 LNK1168 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9437b88b67254a63babf5b72379a760d1ab86062
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541540"
---
# <a name="linker-tools-error-lnk1168"></a>链接器工具错误 LNK1168
无法打开 filename 进行写入  
  
 链接器无法写入 `filename`。 文件可能正在使用中且其文件句柄已被其他进程锁定，或者你可能没有对该文件或者对其所在的目录或网络共享的写入权限。 此错误通常由暂时情况引起，例如，防病毒程序持有的锁文件搜索索引进程，或由 Visual Studio 生成系统持有中释放锁的延迟。  
  
 若要修复此问题，请验证 `filename` 文件句柄是否锁定以及你是否具有对此文件的写入权限。 如果它是可执行文件，则请验证它是否已在运行。  
  
 可以使用 Windows SysInternals 实用工具[处理](http://technet.microsoft.com/sysinternals/bb896655.aspx)或[Process Explorer](http://technet.microsoft.com/sysinternals/bb896653)若要确定哪个进程具有的文件句柄上的锁`filename`。 你还可以使用进程资源管理器释放开放式文件句柄上的锁。 有关如何使用这些实用工具的信息，请参阅它们附带的帮助文件。  
  
 如果文件被防病毒程序锁定，则可以通过防病毒程序从自动扫描中排除生成输出目录，从而修复此问题。 防病毒扫描程序通常当在文件系统中创建新文件时触发，在扫描继续时，它们持有文件上的锁。 有关如何从扫描中排除特定目录的详细信息，请参考防病毒程序文档。  
  
 如果文件被搜索索引服务锁定，则可通过从自动索引中排除生成输出目录来修复此问题。 有关详细信息，请参考索引服务的文档。 若要更改 Windows 搜索索引服务，请使用**索引选项**在 Windows 中**控制面板**。 有关详细信息，请参阅[使用索引改进 Windows 搜索： 常见问题](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7)。  
  
 如果可执行文件无法被生成进程覆盖，则可能被文件资源管理器锁定。 如果**应用程序体验**服务已被禁用，文件资源管理器可能保持的可执行文件句柄锁长一段时间。 若要解决此问题，请运行**services.msc** ，然后打开**属性**对话框**应用程序体验**服务。 更改**启动类型**从**禁用**到**手动**。  
  
## <a name="see-also"></a>请参阅  
 [当你尝试生成解决方案或在 Visual c + + 中的 ActiveX 项目时，可能会收到"错误 PRJ0008"严重错误 LNK1168"错误消息](http://support.microsoft.com/kb/308358)