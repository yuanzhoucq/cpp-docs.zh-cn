---
title: ATL 实用程序引用 |Microsoft Docs
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
ms.openlocfilehash: d11e06b7a8b8bc636de906a210cfffb62c6eeff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220315"
---
# <a name="atl-utilities-reference"></a>ATL 实用程序引用
ATL 提供了代码，用于操作的窗体中的路径和 Url [CPathT](../atl/reference/cpatht-class.md)并[CUrl](../atl/reference/curl-class.md)。 线程池[CThreadPool](../atl/reference/cthreadpool-class.md)，可以在应用程序中使用。 可以在 atlpath.h 和 atlutil.h 中找到此代码。  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[CPathT 类](../atl/reference/cpatht-class.md)|此类表示的路径。|  
|[CDebugReportHook 类](../atl/reference/cdebugreporthook-class.md)|使用此类将调试报告发送到命名管道。|  
|[CNonStatelessWorker 类](../atl/reference/cnonstatelessworker-class.md)|从线程池中接收请求并将它们传递到创建和销毁的工作对象上每个请求。|  
|[CNoWorkerThread 类](../atl/reference/cnoworkerthread-class.md)|使用此类的自变量作为`MonitorClass`到你想要禁用动态缓存维护的缓存类模板参数。|  
|[CThreadPool 类](../atl/reference/cthreadpool-class.md)|此类提供处理的工作项队列的工作线程的池。|  
|[CUrl 类](../atl/reference/curl-class.md)|此类表示的 URL。 它允许您分析现有的 URL 是否处理每个元素独立于其他 URL 的字符串或生成一个从零开始的字符串。|  
|[CWorkerThread 类](../atl/reference/cworkerthread-class.md)|此类创建工作线程或使用现有工作区，等待上一个或多个内核对象句柄，并发出一个句柄的信号时执行指定的客户端函数。|  
  
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
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|此枚举的成员为所理解的方案提供常量[CUrl](../atl/reference/curl-class.md)。|  
  
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

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|此函数是的重载包装器[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
)。 |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函数是的重载包装器[PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)。 |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函数是的重载包装器[PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)。 |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函数是的重载包装器[PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)。 |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函数是的重载包装器[PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)。 |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函数是的重载包装器[PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea)。 |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函数是的重载包装器[PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)。 |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函数是的重载包装器[PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)。 |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函数是的重载包装器[PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)。 |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函数是的重载包装器[PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)。 |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函数是的重载包装器[PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)。 |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函数是的重载包装器[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)。 |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函数是的重载包装器[PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)。 |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函数是的重载包装器[PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya)。 |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函数是的重载包装器[PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)。 |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函数是的重载包装器[PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)。 |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函数是的重载包装器[PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)。 |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函数是的重载包装器[PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)。 |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函数是的重载包装器[PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)。 |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函数是的重载包装器[PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)。 |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函数是的重载包装器[PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)。 |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函数是的重载包装器[PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea)。 |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|此函数是的重载包装器[PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya)。 |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|此函数是的重载包装器[PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca)。 |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|此函数是的重载包装器[PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa)。 |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|此函数是的重载包装器[PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa)。 |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|此函数是的重载包装器[PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa)。 |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|此函数是的重载包装器[PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha)。 |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|此函数是的重载包装器[PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa)。 |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|此函数是的重载包装器[PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona)。 |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|此函数是的重载包装器[PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca)。 |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|此函数是的重载包装器[PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona)。 |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|此函数是的重载包装器[PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota)。 |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|此函数是的重载包装器[PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha)。 |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|此函数是的重载包装器[PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota)。 |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|此函数是的重载包装器[PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa)。 |  
  

## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../atl/atl-com-desktop-components.md)
