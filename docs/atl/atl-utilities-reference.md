---
title: ATL 实用程序引用 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b802d8764dda321e2e313f793f4f2e4745dbcc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atl-utilities-reference"></a>ATL 实用程序引用
ATL 提供有关操作的窗体中的路径和 Url 的代码[CPathT](../atl/reference/cpatht-class.md)和[CUrl](../atl/reference/curl-class.md)。 线程池， [CThreadPool](../atl/reference/cthreadpool-class.md)，可在你的应用程序。 此代码可以 atlpath.h 和 atlutil.h 中找到。  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[CPathT 类](../atl/reference/cpatht-class.md)|此类表示的路径。|  
|[CDebugReportHook 类](../atl/reference/cdebugreporthook-class.md)|使用此类将调试报告发送到命名管道。|  
|[CNonStatelessWorker 类](../atl/reference/cnonstatelessworker-class.md)|从线程池接收请求，并将它们传递到创建和销毁的辅助对象上每个请求。|  
|[CNoWorkerThread 类](../atl/reference/cnoworkerthread-class.md)|使用此类的自变量作为`MonitorClass`如果你想要禁用动态缓存维护缓存类模板参数。|  
|[CThreadPool 类](../atl/reference/cthreadpool-class.md)|此类提供处理的工作项队列的辅助线程的池。|  
|[CUrl 类](../atl/reference/curl-class.md)|此类表示的 URL。 它允许你操纵相互独立地 URL 的每个元素是否分析现有的 URL 字符串或生成一个从零开始的字符串。|  
|[CWorkerThread 类](../atl/reference/cworkerthread-class.md)|此类创建一个工作线程或使用一个现有，等待上一个或多个内核对象句柄，并在其中一个的句柄处于有信号状态时执行指定的客户端函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|专用化[CPathT](../atl/reference/cpatht-class.md)使用`CString`。|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|专用化[CPathT](../atl/reference/cpatht-class.md)使用`CStringA`。|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|专用化[CPathT](../atl/reference/cpatht-class.md)使用`CStringW`。|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|使用的类型[CUrl](../atl/reference/curl-class.md)用于指定端口号。|  
  
### <a name="enums"></a>枚举  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|此枚举的成员为被理解的方案提供常量[CUrl](../atl/reference/curl-class.md)。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|调用此函数可对 URL 进行规范化，包括将不安全的字符和空格转换为转义序列。|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|调用此函数可将基 URL 和相对 URL 合并为单个规范 URL。|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|调用此函数可将所有不安全字符转换为转义序列。|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|调用此函数可获取与特定 internet 协议或方案关联的默认端口号。|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|调用此函数可获取十六进制数字的数值。|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|调用此函数可了解字符在 URL 中能否安全使用。|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|调用此函数可将转义字符转换为其原始值。|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|调用此函数可将系统时间转换为采用适合在 HTTP 标头中使用的格式的字符串。|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|此函数是的重载的包装器[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。 |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函数是的重载的包装器[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。 |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函数是的重载的包装器[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。 |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函数是的重载的包装器[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。 |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函数是的重载的包装器[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。 |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函数是的重载的包装器[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。 |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函数是的重载的包装器[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。 |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函数是的重载的包装器[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。 |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函数是的重载的包装器[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。 |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函数是的重载的包装器[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。 |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函数是的重载的包装器[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。 |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函数是的重载的包装器[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。 |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函数是的重载的包装器[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。 |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函数是的重载的包装器[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。 |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函数是的重载的包装器[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。 |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函数是的重载的包装器[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。 |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函数是的重载的包装器[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。 |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函数是的重载的包装器[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。 |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函数是的重载的包装器[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。 |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函数是的重载的包装器[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。 |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函数是的重载的包装器[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。 |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函数是的重载的包装器[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。 |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|此函数是的重载的包装器[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。 |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|此函数是的重载的包装器[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。 |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|此函数是的重载的包装器[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。 |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|此函数是的重载的包装器[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。 |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|此函数是的重载的包装器[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。 |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|此函数是的重载的包装器[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。 |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|此函数是的重载的包装器[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。 |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|此函数是的重载的包装器[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。 |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|此函数是的重载的包装器[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。 |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|此函数是的重载的包装器[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。 |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|此函数是的重载的包装器[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。 |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|此函数是的重载的包装器[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。 |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|此函数是的重载的包装器[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。 |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|此函数是的重载的包装器[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。 |  
  

## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../atl/atl-com-desktop-components.md)
