---
title: "ATL 实用程序引用 | Microsoft Docs"
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
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ATL 实用程序引用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 [CPathT](../atl/reference/cpatht-class.md) 和 [卷毛](../atl/reference/curl-class.md)形式，ATL提供操作的路径提供代码和URL。  线程池，[CThreadPool](../atl/reference/cthreadpool-class.md)，可用于您的应用程序。  此代码可在atlpath.h和atlutil.h找到。  
  
### 类  
  
|||  
|-|-|  
|[CPathT选件类](../atl/reference/cpatht-class.md)|此选件类表示路径。|  
|[CDebugReportHook选件类](../atl/reference/cdebugreporthook-class.md)|使用此选件类发送调试报告为命名管道。|  
|[CNonStatelessWorker选件类](../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求并传递到在每个请求创建和销毁的辅助对象。|  
|[CNoWorkerThread选件类](../atl/reference/cnoworkerthread-class.md)|如果想要禁用动态缓存维护，请使用此选件类作为参数。`MonitorClass` 模板参数传递到缓存选件类。|  
|[CThreadPool选件类](../atl/reference/cthreadpool-class.md)|此选件类提供的辅助线程池处理工作项队列。|  
|[右选件类](../atl/reference/curl-class.md)|此选件类表示URL。  它是否可以独立于其他操作URL的每个元素分析现有的URL字符串或从头开始生成字符串。|  
|[CWorkerThread选件类](../atl/reference/cworkerthread-class.md)|当其中一个处理事件信号时，此选件类在一个或多个核心对象处理创建辅助线程或使用现有工作项，等待，并执行一个指定的客户端功能。|  
  
### Typedef  
  
|||  
|-|-|  
|[CPath](../Topic/CPath.md)|[CPathT](../atl/reference/cpatht-class.md) 的专用化使用 `CString`的。|  
|[CPathA](../Topic/CPathA.md)|[CPathT](../atl/reference/cpatht-class.md) 的专用化使用 `CStringA`的。|  
|[CPathW](../Topic/CPathW.md)|[CPathT](../atl/reference/cpatht-class.md) 的专用化使用 `CStringW`的。|  
|[ATL\_URL\_PORT](../Topic/ATL_URL_PORT.md)|[卷毛](../atl/reference/curl-class.md) 使用的类型指定端口号。|  
  
### 枚举  
  
|||  
|-|-|  
|[ATL\_URL\_SCHEME](../Topic/ATL_URL_SCHEME.md)|此枚举的成员为 [卷毛](../atl/reference/curl-class.md)了解架构提供常数。|  
  
### 函数  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md)|调用此函数教规本地化URL，包括转换不安全的字符和空格转换为转义序列。|  
|[AtlCombineUrl](../Topic/AtlCombineUrl.md)|调用此函数将基URL和相对URL到一个，指定URL。|  
|[AtlEscapeUrl](../Topic/AtlEscapeUrl.md)|调用此函数将所有不安全的字符转换为转义序列。|  
|[AtlGetDefaultUrlPort](../Topic/AtlGetDefaultUrlPort.md)|调用此函数获取默认端口号与特定internet协议或模式。|  
|[AtlHexValue](../Topic/AtlHexValue.md)|调用此函数获取一个十六进制数字的数值。|  
|[AtlIsUnsafeUrlChar](../Topic/AtlIsUnsafeUrlChar.md)|调用此函数查看字符是否是安全的用于URL。|  
|[AtlUnescapeUrl](../Topic/AtlUnescapeUrl.md)|调用此函数转换转义字符回其原始值。|  
|[SystemTimeToHttpDate](../Topic/SystemTimeToHttpDate.md)|调用此函数将系统时间转换为字符串了适当的格式在HTTP标头。|  
|[ATLPath::AddBackslash](../Topic/ATLPath::AddBackslash.md)|此函数是 [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)的重载包装。|  
|[ATLPath::AddExtension](../Topic/ATLPath::AddExtension.md)|此函数是 [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)的重载包装。|  
|[ATLPath::Append](../Topic/ATLPath::Append.md)|此函数是 [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)的重载包装。|  
|[ATLPath::BuildRoot](../Topic/ATLPath::BuildRoot.md)|此函数是 [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)的重载包装。|  
|[ATLPath::Canonicalize](../Topic/ATLPath::Canonicalize.md)|此函数是 [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)的重载包装。|  
|[ATLPath::Combine](../Topic/ATLPath::Combine.md)|此函数是 [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)的重载包装。|  
|[ATLPath::CommonPrefix](../Topic/ATLPath::CommonPrefix.md)|此函数是 [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)的重载包装。|  
|[ATLPath::CompactPath](../Topic/ATLPath::CompactPath.md)|此函数是 [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)的重载包装。|  
|[ATLPath::CompactPathEx](../Topic/ATLPath::CompactPathEx.md)|此函数是 [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)的重载包装。|  
|[ATLPath::FileExists](../Topic/ATLPath::FileExists.md)|此函数是 [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)的重载包装。|  
|[ATLPath::FindExtension](../Topic/ATLPath::FindExtension.md)|此函数是 [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)的重载包装。|  
|[ATLPath::FindFileName](../Topic/ATLPath::FindFileName.md)|此函数是 [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)的重载包装。|  
|[ATLPath::GetDriveNumber](../Topic/ATLPath::GetDriveNumber.md)|此函数是 [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)的重载包装。|  
|[ATLPath::IsDirectory](../Topic/ATLPath::IsDirectory.md)|此函数是 [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)的重载包装。|  
|[ATLPath::IsFileSpec](../Topic/ATLPath::IsFileSpec.md)|此函数是 [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)的重载包装。|  
|[ATLPath::IsPrefix](../Topic/ATLPath::IsPrefix.md)|此函数是 [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)的重载包装。|  
|[ATLPath::IsRelative](../Topic/ATLPath::IsRelative.md)|此函数是 [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)的重载包装。|  
|[ATLPath::IsRoot](../Topic/ATLPath::IsRoot.md)|此函数是 [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)的重载包装。|  
|[ATLPath::IsSameRoot](../Topic/ATLPath::IsSameRoot.md)|此函数是 [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)的重载包装。|  
|[ATLPath::IsUNC](../Topic/ATLPath::IsUNC.md)|此函数是 [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)的重载包装。|  
|[ATLPath::IsUNCServer](../Topic/ATLPath::IsUNCServer.md)|此函数是 [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)的重载包装。|  
|[ATLPath::IsUNCServerShare](../Topic/ATLPath::IsUNCServerShare.md)|此函数是 [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)的重载包装。|  
|[ATLPath::MakePretty](../Topic/ATLPath::MakePretty.md)|此函数是 [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)的重载包装。|  
|[ATLPath::MatchSpec](../Topic/ATLPath::MatchSpec.md)|此函数是 [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)的重载包装。|  
|[ATLPath::QuoteSpaces](../Topic/ATLPath::QuoteSpaces.md)|此函数是 [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)的重载包装。|  
|[ATLPath::RelativePathTo](../Topic/ATLPath::RelativePathTo.md)|此函数是 [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)的重载包装。|  
|[ATLPath::RemoveArgs](../Topic/ATLPath::RemoveArgs.md)|此函数是 [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)的重载包装。|  
|[ATLPath::RemoveBackslash](../Topic/ATLPath::RemoveBackslash.md)|此函数是 [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)的重载包装。|  
|[ATLPath::RemoveBlanks](../Topic/ATLPath::RemoveBlanks.md)|此函数是 [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)的重载包装。|  
|[ATLPath::RemoveExtension](../Topic/ATLPath::RemoveExtension.md)|此函数是 [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)的重载包装。|  
|[ATLPath::RemoveFileSpec](../Topic/ATLPath::RemoveFileSpec.md)|此函数是 [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)的重载包装。|  
|[ATLPath::RenameExtension](../Topic/ATLPath::RenameExtension.md)|此函数是 [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)的重载包装。|  
|[ATLPath::SkipRoot](../Topic/ATLPath::SkipRoot.md)|此函数是 [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)的重载包装。|  
|[ATLPath::StripPath](../Topic/ATLPath::StripPath.md)|此函数是 [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)的重载包装。|  
|[ATLPath::StripToRoot](../Topic/ATLPath::StripToRoot.md)|此函数是 [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)的重载包装。|  
|[ATLPath::UnquoteSpaces](../Topic/ATLPath::UnquoteSpaces.md)|此函数是 [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)的重载包装。|  
  
### 宏  
  
|||  
|-|-|  
|[ATL\_URL标志](../Topic/ATL_URL%20Flags.md)|这些标志修改 [AtlEscapeUrl](../Topic/AtlEscapeUrl.md) 和 [AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md) 行为。|  
|[ATL\_WORKER\_THREAD\_WAIT](../Topic/ATL_WORKER_THREAD_WAIT.md)|此宏以毫秒为单位定义默认 [CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md) 将等待辅助线程关闭。|  
|[ATLS\_DEFAULT\_THREADPOOLSHUTDOWNTIMEOUT](../Topic/ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT.md)|此宏以毫秒为单位定义默认时间 [CThreadPool](../atl/reference/cthreadpool-class.md) 将等待线程关闭。|  
|[ATLS\_DEFAULT\_THREADSPERPROC](../Topic/ATLS_DEFAULT_THREADSPERPROC.md)|此宏定义线程的默认周期数每个 [CThreadPool](../atl/reference/cthreadpool-class.md)使用的处理器。|  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)