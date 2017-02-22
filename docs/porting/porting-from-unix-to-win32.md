---
title: "从 UNIX 到 Win32 的迁移 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "APIs [C++], porting to Win32"
  - "migration [C++]"
  - "porting to Win32 [C++]"
  - "porting to Win32 [C++], from UNIX"
  - "UNIX [C++], porting to Win32"
  - "Win32 applications [C++], migrating from UNIX"
  - "Windows API [C++], migrating from UNIX"
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 从 UNIX 到 Win32 的迁移
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将应用程序从 UNIX 迁移到 Windows 时，有以下几个选项：  
  
-   使用 UNIX 库来将应用程序从 UNIX 迁移到 Win32  
  
-   在本机将应用程序从 UNIX 迁移到 Win32  
  
-   使用 POSIX 子系统在 Windows 上运行 UNIX 应用程序  
  
## UNIX 库  
 UNIX 程序员通常考虑使用类似于 UNIX 库的第三方库来将 UNIX 代码编译为 Win32 可执行文件。  有几个商用（和至少一个公共域）库可以执行此操作。  此选项可用于一些应用程序。  这些迁移库的优点在于最大限度地减少了初始迁移工作量。  对于有竞争力的软件产品来说，其主要缺点是应用程序的本机 Win32 端口通常速度更快并必然拥有更多功能。  如果应用程序需要执行 Win32 调用以从 Windows 中获取更多资源，则很难冲出其 UNIX 外壳。  
  
 下表为迁移和支持 UNIX 到 Visual C\+\+ 的迁移提供了 Microsoft 和第三方资源：  
  
### UNIX 迁移指南  
 《UNIX 自定义应用程序迁移指南》为从 UNIX 到 Win32 环境的代码迁移提供了技术帮助。  
  
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=95428](http://go.microsoft.com/fwlink/?LinkId=95428)  
  
 《Unix 迁移项目指南》对《UNIX 自定义应用程序迁移指南》进行了补充，在从 UNIX 到 Win32 迁移大量项目方面提供了高级帮助。  该指南针对项目迁移的各个阶段中要考虑的问题提供了相应建议。  该指南可从以下地址下载：  
  
 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=20012](http://go.microsoft.com/fwlink/?linkid=20012)  
  
### Microsoft Windows Services for UNIX \(SFU\)  
 Microsoft Windows Services for UNIX \(SFU\) 提供了一系列完整的用于将 Windows 集成到基于 UNIX 的现有环境的跨平台服务。  面向 UNIX 的服务提供文件共享、远程访问和管理、密码同步、公共目录管理、一组常用的实用工具和一个外壳。  
  
 [Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### InteropSystems.com  
 [http:\/\/www.interopsystems.com\/](http://www.interopsystems.com/)  
  
 为公司提供从 UNIX 迁移到 Win32 的软件支持的第三方站点。  
  
### C\+\+ Boost 网站  
 [http:\/\/boost.sourceforge.net\/regression\-logs\/](http://boost.sourceforge.net/regression-logs/)  
  
 [http:\/\/boost.sourceforge.net\/boost\-build2\/](http://boost.sourceforge.net/boost-build2/)  
  
## 将 UNIX 应用程序直接迁移到 Win32  
 另一种方法是将 UNIX 应用程序直接迁移到 Win32。  借助 ANSI C\/C\+\+ 库和商用 C 编译器库，Win32 应用程序中提供了很多 UNIX 应用程序依赖的传统系统调用。  
  
 无需更改基于 **stdio** 的应用程序的输出模型，因为 Win32 控制台 API 会模拟 **stdio** 模型，而且存在使用 Win32 控制台 API 的 *curses* 版本。  有关详细信息，请参阅 [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025)。  
  
 基于 Berkeley 套接字的应用程序需要稍做更改，以便像 Win32 应用程序一样运行。  Windows 套接字接口旨在通过 WinSock 规范的介绍部分中所述稍作更改，实现与 BSD 套接字的可移植性。  
  
 Windows 支持符合 DCE 的 RPC，因此基于 RPC 的应用程序便于使用。  请参阅 [RPC 函数](http://msdn.microsoft.com/library/windows/desktop/aa378623)。  
  
 其中的一个最大差异在于进程模型。  UNIX 具有 **fork**；Win32 却没有。  根据使用的 **fork** 和基本代码，Win32 可使用两种 API：**CreateProcess** 和 `CreateThread`。  可在 Win32 中修改其自行派生了多个副本的 UNIX 应用程序，使其拥有多个进程或一个具有多个线程的进程。  如果使用多个进程，则可使用多个 IPC 方法在进程之间进行通信（如果需要 **fork** 提供的功能，可能还可以将新进程的代码和数据更新为如父级一样）。  有关 IPC 的详细信息，请参阅[进程间通信](http://msdn.microsoft.com/library/windows/desktop/aa365574)。  
  
 Windows 和 UNIX 图形模型有很大差异。  UNIX 使用 X 窗口系统 GUI，而 Windows 使用 GDI。  尽管在概念上类似，但无法从 X API 简单映射到 GDI API。  但是，OpenGL 支持可用于迁移基于 UNIX OpenGL 的应用程序。  还有针对 Windows 的 X 客户端和 X 服务器。  请参阅[设备上下文](http://msdn.microsoft.com/library/windows/desktop/dd183553)以获取 GDI 的相关信息。  
  
 基本 UNIX 应用程序（包括许多 CGI 应用程序）应轻松地迁移到 Windows 上运行的 Visual C\+\+。  诸如 **open**、`fopen`**read**、**write** 等功能在 Visual C\+\+ 运行时库中可用。  此外，C UNIX API 和 Win32 API 之间存在一对一映射：**open** 对应 **CreateFile**、**read** 对应 **ReadFile**、**write** 对应 **WriteFile**、`ioctl` 对应 **DeviceIOControl**，而 **close** 对应 **CloseFile** 等等。  
  
## Windows POSIX 子系统  
 UNIX 程序员考虑的另一个选项是 Windows POSIX 子系统。  但是，它仅支持 POSIX 1003.1 版本，这是在创建 Windows NT 时唯一标准化的 POSIX 版本。  自那时起，几乎不存在要扩展此子系统的需求，因为大多数应用程序已转换为 Win32。  1003.1 系统对功能完整的应用程序没有太大吸引力，因为它不具备的功能有很多（如 1003.2 中的功能、网络支持等）。   Windows POSIX 子系统下运行的功能完整的应用程序无权访问可用于 Win32 应用程序的 Windows 功能，例如内存映射文件、联网和图形。  VI、LS 和 GREP 等应用程序是 Windows POSIX 子系统的主要目标。  
  
## 请参阅  
 [移植程序](http://msdn.microsoft.com/zh-cn/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)   
 [UNIX](../c-runtime-library/unix.md)   
 [推理规则](../build/inference-rules.md)