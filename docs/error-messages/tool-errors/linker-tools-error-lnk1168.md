---
title: "链接器工具错误 LNK1168 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1168"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1168"
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 链接器工具错误 LNK1168
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开 filename 进行写入  
  
 链接器无法写入 `filename`。  文件可能正在使用中且其文件句柄已被其他进程锁定，或者你可能没有对该文件或者对其所在的目录或网络共享的写入权限。  此错误通常由瞬间条件造成。例如，防病毒程序持有的锁、文件搜索索引进程或释放 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 生成系统持有的锁时的延迟。  
  
 若要修复此问题，请验证 `filename` 文件句柄是否锁定以及你是否具有对此文件的写入权限。  如果它是可执行文件，则请验证它是否已在运行。  
  
 也可以使用 Windows SysInternals 工具 [Handle](http://technet.microsoft.com/sysinternals/bb896655.aspx) 或 [Process Explorer](http://technet.microsoft.com/sysinternals/bb896653) 来确定哪个进程在 `filename` 上具有文件句柄锁。  你还可以使用进程资源管理器释放开放式文件句柄上的锁。  有关如何使用这些实用工具的信息，请参阅它们附带的帮助文件。  
  
 如果文件被防病毒程序锁定，则可以通过防病毒程序从自动扫描中排除生成输出目录，从而修复此问题。  防病毒扫描程序通常当在文件系统中创建新文件时触发，在扫描继续时，它们持有文件上的锁。  有关如何从扫描中排除特定目录的详细信息，请参考防病毒程序文档。  
  
 如果文件被搜索索引服务锁定，则可通过从自动索引中排除生成输出目录来修复此问题。  有关详细信息，请参考索引服务的文档。  若要更改 Windows 搜索索引服务，请使用 Windows**“控制面板”**中的**“索引选项”**。  有关详细信息，请参阅[使用索引改进 Windows 搜索：常见问题](http://windows.microsoft.com/zh-cn/windows/improve-windows-searches-using-index-faq#1TC=windows-7)。  
  
 如果可执行文件无法被生成进程覆盖，则可能被文件资源管理器锁定。  如果已禁用**“应用程序体验”**服务，则文件资源管理器可能延长可执行文件句柄锁定的时间。  若要修复此问题，请运行 **services.msc** 然后打开**“应用程序体验”**服务的**“属性”**对话框。  将**“启动类型”**从**“已禁用”**更改为**“手动”**。  
  
## 请参阅  
 [当你尝试在 Visual C\+\+ 中生成解决方案或 ActiveX 项目时，可能收到“错误 PRJ0008”或“严重错误 LNK1168”错误消息](http://support.microsoft.com/kb/308358)