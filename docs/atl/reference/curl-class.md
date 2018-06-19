---
title: CUrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afb0f7abc079d699cfcf682356b88b9cc8aa2bb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366229"
---
# <a name="curl-class"></a>CUrl 类
此类表示的 URL。 它允许你操纵相互独立地 URL 的每个元素是否分析现有的 URL 字符串或生成一个从零开始的字符串。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CUrl
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|构造函数。|  
|[CUrl:: ~ CUrl](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|调用此方法以将 URL 字符串转换为规范格式。|  
|[CUrl::Clear](#clear)|调用此方法以清除所有 URL 字段。|  
|[CUrl::CrackUrl](#crackurl)|调用此方法解码和分析的 URL。|  
|[CUrl::CreateUrl](#createurl)|调用此方法以创建 URL。|  
|[CUrl::GetExtraInfo](#getextrainfo)|调用此方法以获取额外信息 (如*文本*或 #*文本*) 从该 URL。|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|调用此方法以获取额外信息的长度 (如*文本*或 #*文本*) 以从 URL 检索。|  
|[CUrl::GetHostName](#gethostname)|调用此方法以从 URL 中获取的主机名。|  
|[CUrl::GetHostNameLength](#gethostnamelength)|调用此方法以获取主机名的长度。|  
|[CUrl::GetPassword](#getpassword)|调用此方法以从 URL 中获取密码。|  
|[CUrl::GetPasswordLength](#getpasswordlength)|调用此方法以获取密码的长度。|  
|[CUrl::GetPortNumber](#getportnumber)|调用此方法以获取在 ATL_URL_PORT 方面的端口号。|  
|[CUrl::GetScheme](#getscheme)|调用此方法以获取 URL 方案。|  
|[CUrl::GetSchemeName](#getschemename)|调用此方法以获取的 URL 方案名称。|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|调用此方法要获取的 URL 方案名称的长度。|  
|[CUrl::GetUrlLength](#geturllength)|调用此方法以获取 URL 长度。|  
|[CUrl::GetUrlPath](#geturlpath)|调用此方法来获取的 URL 路径。|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|调用此方法以获取的 URL 路径长度。|  
|[CUrl::GetUserName](#getusername)|调用此方法以获取从 URL 的用户名。|  
|[CUrl::GetUserNameLength](#getusernamelength)|调用此方法以获取用户名称的长度。|  
|[CUrl::SetExtraInfo](#setextrainfo)|调用此方法以设置额外的信息 (如*文本*或 #*文本*) 的 URL。|  
|[CUrl::SetHostName](#sethostname)|调用此方法用于设置主机名。|  
|[CUrl::SetPassword](#setpassword)|调用此方法以设置密码。|  
|[CUrl::SetPortNumber](#setportnumber)|调用此方法以设置在 ATL_URL_PORT 方面的端口号。|  
|[CUrl::SetScheme](#setscheme)|调用此方法以设置 URL 方案。|  
|[CUrl::SetSchemeName](#setschemename)|调用此方法以设置 URL 方案名称。|  
|[CUrl::SetUrlPath](#seturlpath)|调用此方法以设置的 URL 路径。|  
|[CUrl::SetUserName](#setusername)|调用此方法以设置用户名。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|将分配指定`CUrl`对象与当前`CUrl`对象。|  
  
## <a name="remarks"></a>备注  
 `CUrl` 允许您将操作的 URL，例如路径或端口号的字段。 `CUrl` 理解以下形式的 Url:  
  
 \<方案 >://\<用户名 >:\<密码 > @\<主机名 >:\<端口号 > /\<UrlPath >\<ExtraInfo >  
  
 （某些字段是可选的。）例如，考虑此 URL:  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl)对其进行分析，如下所示：  
  
-   方案:"http"或[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   用户名:"someone"  
  
-   密码:"密码"  
  
-   主机名:"www.microsoft.com"  
  
-   端口号： 80  
  
-   UrlPath:"visualc/stuff.htm"  
  
-   ExtraInfo:"#contents"  
  
 要操作 UrlPath 字段 （例如），你可以使用[GetUrlPath](#geturlpath)， [GetUrlPathLength](#geturlpathlength)，和[SetUrlPath](#seturlpath)。 你将使用[CreateUrl](#createurl)若要创建完整的 URL 字符串。  
  
## <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
##  <a name="canonicalize"></a>  CUrl::Canonicalize  
 调用此方法以将 URL 字符串转换为规范格式。  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 控制规范化标志。 如果未不指定任何标志 ( `dwFlags` = 0)，该方法将所有不安全的字符和元序列 (如\\。，\...，和\\...) 进行转义序列。 `dwFlags` 可以是以下值之一：  
  
-   ATL_URL_BROWSER_MODE： 不会进行编码或解码后"#"字符或""并不会删除尾随空格后""。 如果未指定此值，编码整个 URL，并且会删除尾随空格。  
  
-   ATL_URL _DECODE： 将所有 %xx 序列都转换为字符，包括转义序列前分析该 URL。  
  
-   ATL_URL _ENCODE_PERCENT： 将遇到任何百分号编码。 默认情况下，不进行编码百分比符号的组合。  
  
-   ATL_URL _ENCODE_SPACES_ONLY： 将仅空格编码。  
  
-   ATL_URL _NO_ENCODE： 不转换不安全的字符进行转义序列。  
  
-   ATL_URL _NO_META： 不会删除元序列 (如"。"和"..") 从该 URL。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 将转换为规范格式包括将转换不安全字符和空格为转义序列。  
  
##  <a name="clear"></a>  CUrl::Clear  
 调用此方法以清除所有 URL 字段。  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>  CUrl::CrackUrl  
 调用此方法解码和分析的 URL。  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszUrl`  
 URL。  
  
 `dwFlags`  
 指定要转换中的所有转义字符的 ATL_URL_DECODE 或 ATL_URL_ESCAPE`lpszUrl`为分析后其实际值。 （在 Visual c + + 2005 中之前, ATL_URL_DECODE 转换所有转义字符分析之前。）  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="createurl"></a>  CUrl::CreateUrl  
 此方法构造 CUrl 对象的组件字段从一个 URL 字符串。  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszUrl*  
 字符串缓冲区来保存完整的 URL 字符串。  
  
 `pdwMaxLength`  
 最大长度*lpszUrl*字符串缓冲区。  
  
 `dwFlags`  
 指定 ATL_URL_ESCAPE 要转换中的所有转义字符*lpszUrl*为其实际值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此方法将其各个字段追加为了构建完整的 URL 字符串使用以下格式：  
  
 **\<方案 >://\<用户 >:\<传递 > @\<域 >:\<端口 >\<路径 >\<额外 >**  
  
 调用此方法时`pdwMaxLength`参数最初应包含引用的字符串缓冲区的最大长度*lpszUrl*参数。 值`pdwMaxLength`参数将使用的 URL 字符串的实际长度的更新。  
  
### <a name="example"></a>示例  
 此示例演示如何创建 CUrl 对象和检索其 URL 字符串  
  
 [!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>  CUrl::CUrl  
 构造函数。  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>参数  
 `urlThat`  
 `CUrl`对象，若要复制到创建 URL。  
  
##  <a name="dtor"></a>  CUrl:: ~ CUrl  
 析构函数。  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo  
 调用此方法以获取额外信息 (如*文本*或 #*文本*) 从该 URL。  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含额外信息的字符串。  
  
##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength  
 调用此方法以获取额外信息的长度 (如*文本*或 #*文本*) 以从 URL 检索。  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回包含额外信息的字符串的长度。  
  
##  <a name="gethostname"></a>  CUrl::GetHostName  
 调用此方法以从 URL 中获取的主机名。  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的主机名。  
  
##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength  
 调用此方法以获取主机名的长度。  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回主机名称长度。  
  
##  <a name="getpassword"></a>  CUrl::GetPassword  
 调用此方法以从 URL 中获取密码。  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回密码。  
  
##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength  
 调用此方法以获取密码的长度。  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回密码长度。  
  
##  <a name="getportnumber"></a>  CUrl::GetPortNumber  
 调用此方法以获取端口号。  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的端口号。  
  
##  <a name="getscheme"></a>  CUrl::GetScheme  
 调用此方法以获取 URL 方案。  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回[ATL_URL_SCHEME](atl-url-scheme-enum.md)值，该值描述 URL 的方案。  
  
##  <a name="getschemename"></a>  CUrl::GetSchemeName  
 调用此方法以获取的 URL 方案名称。  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 URL 方案名称 （例如"http"或"ftp"）。  
  
##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength  
 调用此方法要获取的 URL 方案名称的长度。  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 URL 方案名称的长度。  
  
##  <a name="geturllength"></a>  CUrl::GetUrlLength  
 调用此方法以获取 URL 长度。  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 URL 长度。  
  
##  <a name="geturlpath"></a>  CUrl::GetUrlPath  
 调用此方法来获取的 URL 路径。  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的 URL 路径。  
  
##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength  
 调用此方法以获取的 URL 路径长度。  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的 URL 路径长度。  
  
##  <a name="getusername"></a>  CUrl::GetUserName  
 调用此方法以获取从 URL 的用户名。  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的用户名称。  
  
##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength  
 调用此方法以获取用户名称的长度。  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回用户名称的长度。  
  
##  <a name="operator_eq"></a>  CUrl::operator =  
 将分配指定`CUrl`对象与当前`CUrl`对象。  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>参数  
 `urlThat`  
 `CUrl`对象将复制到当前对象。  
  
### <a name="return-value"></a>返回值  
 返回对当前对象的引用。  
  
##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo  
 调用此方法以设置额外的信息 (如*文本*或 #*文本*) 的 URL。  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszInfo*  
 包含要在 URL 中包括的额外信息的字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="sethostname"></a>  CUrl::SetHostName  
 调用此方法用于设置主机名。  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszHost`  
 主机名中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="setpassword"></a>  CUrl::SetPassword  
 调用此方法以设置密码。  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszPass*  
 密码。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="setportnumber"></a>  CUrl::SetPortNumber  
 调用此方法以设置的端口号。  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>参数  
 *nPrt*  
 端口号。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="setscheme"></a>  CUrl::SetScheme  
 调用此方法以设置 URL 方案。  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>参数  
 `nScheme`  
 之一[ATL_URL_SCHEME](atl-url-scheme-enum.md)方案的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此外可以按名称设置方案 (请参阅[CUrl::SetSchemeName](#setschemename))。  
  
##  <a name="setschemename"></a>  CUrl::SetSchemeName  
 调用此方法以设置 URL 方案名称。  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszSchm*  
 URL 方案名称。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此外可以通过使用设置方案[ATL_URL_SCHEME](atl-url-scheme-enum.md)常量 (请参阅[CUrl::SetScheme](#setscheme))。  
  
##  <a name="seturlpath"></a>  CUrl::SetUrlPath  
 调用此方法以设置的 URL 路径。  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpszPath`  
 URL 路径中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
##  <a name="setusername"></a>  CUrl::SetUserName  
 调用此方法以设置用户名。  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>参数  
 *lpszUser*  
 用户名。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
## <a name="see-also"></a>请参阅  
 [类](../../atl/reference/atl-classes.md)
