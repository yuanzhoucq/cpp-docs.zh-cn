---
title: ATL 实用程序引用
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 6c1481929f832e6f810ce46773f328f278b503fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491705"
---
# <a name="atl-utilities-reference"></a>ATL 实用程序引用

ATL 提供以[CPathT](../atl/reference/cpatht-class.md)和[卷曲](../atl/reference/curl-class.md)形式操作路径和 url 的代码。 可以在应用程序中使用线程池[CThreadPool](../atl/reference/cthreadpool-class.md)。 可在 atlpath.h 和 atlutil.h 中找到此代码。

### <a name="classes"></a>类

|||
|-|-|
|[CPathT 类](../atl/reference/cpatht-class.md)|此类表示一个路径。|
|[CDebugReportHook 类](../atl/reference/cdebugreporthook-class.md)|使用此类可将调试报告发送到命名管道。|
|[CNonStatelessWorker 类](../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求, 并将其传递到在每个请求上创建并销毁的辅助角色对象。|
|[CNoWorkerThread 类](../atl/reference/cnoworkerthread-class.md)|如果要禁用动态缓存维护, 请`MonitorClass`使用此类作为用于缓存类的模板参数的参数。|
|[CThreadPool 类](../atl/reference/cthreadpool-class.md)|此类提供处理工作项队列的工作线程池。|
|[CUrl 类](../atl/reference/curl-class.md)|此类表示一个 URL。 它使您可以独立于其他元素处理 URL 的每个元素, 无论是分析现有的 URL 字符串还是从头开始生成字符串。|
|[CWorkerThread 类](../atl/reference/cworkerthread-class.md)|此类创建一个或多个工作线程, 并使用现有的工作线程, 在一个或多个内核对象句柄上等待, 并在其中一个句柄发出信号时执行指定的客户端函数。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|使用`CString`的[CPathT](../atl/reference/cpatht-class.md)的专用化。|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|使用`CStringA`的[CPathT](../atl/reference/cpatht-class.md)的专用化。|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|使用`CStringW`的[CPathT](../atl/reference/cpatht-class.md)的专用化。|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|用于指定端口号的[卷](../atl/reference/curl-class.md)的类型。|

### <a name="enums"></a>枚举

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|此枚举的成员为[曲线](../atl/reference/curl-class.md)理解的方案提供常数。|

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
)。 | |[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函数是的重载包装器[PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。 | |[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函数是的重载包装器[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。 | |[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函数是的重载包装器[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。 | |[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函数是的重载包装器[PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。 | |[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函数是的重载包装器[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。 | |[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函数是的重载包装器[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。 | |[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函数是的重载包装器[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。 | |[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函数是的重载包装器[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。 | |[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函数是的重载包装器[PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。 | |[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函数是的重载包装器[PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。 | |[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函数是的重载包装器[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。 | |[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函数是的重载包装器[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。 | |[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函数是的重载包装器[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。 | |[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函数是的重载包装器[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。 | |[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函数是的重载包装器[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。 | |[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函数是的重载包装器[PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。 | |[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函数是的重载包装器[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。 | |[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函数是的重载包装器[PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。 | |[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函数是的重载包装器[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。 | |[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函数是的重载包装器[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。 | |[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函数是的重载包装器[PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../atl/atl-com-desktop-components.md)
