---
title: CUrl 类
ms.date: 05/06/2019
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
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330472"
---
# <a name="curl-class"></a>CUrl 类

此类表示 URL。 它允许您独立于其他元素操作 URL 的每个元素，无论是分析现有 URL 字符串还是从头开始构建字符串。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CUrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[Url：：CUrl](#curl)|构造函数。|
|[Url：_CUrl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[库尔：：规范化](#canonicalize)|调用此方法将 URL 字符串转换为规范形式。|
|[Url：：清除](#clear)|调用此方法以清除所有 URL 字段。|
|[Url：：裂纹](#crackurl)|调用此方法来解码和分析 URL。|
|[Url：：创建 Url](#createurl)|调用此方法以创建 URL。|
|[Url：获取额外信息](#getextrainfo)|调用此方法从 URL 获取额外信息（如*文本*或 +*文本*）。|
|[Url：获取额外信息长度](#getextrainfolength)|调用此方法获取从 URL 检索的额外信息（如*文本*或 #*文本*）的长度。|
|[Url：获取主机名称](#gethostname)|调用此方法从 URL 获取主机名。|
|[Url：获取主机名称长度](#gethostnamelength)|调用此方法以获取主机名的长度。|
|[Url：获取密码](#getpassword)|调用此方法从 URL 获取密码。|
|[Url：获取密码长度](#getpasswordlength)|调用此方法获取密码的长度。|
|[Url：获取端口号](#getportnumber)|调用此方法以获取端口号ATL_URL_PORT。|
|[Url：获取方案](#getscheme)|调用此方法获取 URL 方案。|
|[Url：获取计划名称](#getschemename)|调用此方法获取 URL 方案名称。|
|[Url：获取方案名称长度](#getschemenamelength)|调用此方法获取 URL 方案名称的长度。|
|[Url：获取 Url 长度](#geturllength)|调用此方法以获取 URL 长度。|
|[Url：获取 UrlPath](#geturlpath)|调用此方法以获取 URL 路径。|
|[Url：获取 Url 路径长度](#geturlpathlength)|调用此方法以获取 URL 路径长度。|
|[Url：获取用户名](#getusername)|调用此方法从 URL 获取用户名。|
|[Url：获取用户名长度](#getusernamelength)|调用此方法以获取用户名的长度。|
|[Url：：设置额外信息](#setextrainfo)|调用此方法以设置 URL 的额外信息（如*文本*或 #*文本*）。|
|[Url：：设置主机名称](#sethostname)|调用此方法以设置主机名。|
|[Url：：设置密码](#setpassword)|调用此方法以设置密码。|
|[Url：：设置端口号](#setportnumber)|调用此方法以按ATL_URL_PORT设置端口号。|
|[Url：：设置方案](#setscheme)|调用此方法以设置 URL 方案。|
|[Url：：设置方案名称](#setschemename)|调用此方法以设置 URL 方案名称。|
|[Url：：设置 Url 路径](#seturlpath)|调用此方法以设置 URL 路径。|
|[Url：：设置用户名](#setusername)|调用此方法以设置用户名。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[Url：：运算符 |](#operator_eq)|将指定`CUrl`对象分配给当前`CUrl`对象。|

## <a name="remarks"></a>备注

`CUrl`允许您操作 URL 的字段，如路径或端口号。 `CUrl`了解以下形式的 URL：

\<方案>：//\<用户名>：\<密码>\@\<主机名>：\<端口号>/UrlPath\< \<>附加信息>

（某些字段是可选的。例如，请考虑以下 URL：

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[Url：：ClackUrl](#crackurl)解析它如下：

- 方案："http"或[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- 用户名："某人"

- 密码："机密"

- 主机名："`www.microsoft.com`"

- 端口号： 80

- UrlPath："visualc/stuff.htm"

- 附加信息："#contents"

要操作 UrlPath 字段（例如），可以使用[GetUrlPath、GetUrlPath](#geturlpath)[长度](#geturlpathlength)和[SetUrlPath](#seturlpath)。 您可以使用[CreateUrl](#createurl)创建完整的 URL 字符串。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>库尔：：规范化

调用此方法将 URL 字符串转换为规范形式。

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

dwFlags**<br/>
控制规范化的标志。 如果未指定标志 *（dwFlags* = 0），该方法将所有不安全的字符和元序列（如\\.、* . 和\\.） 转换为转义序列。 *dwFlags*可以是以下值之一：

- ATL_URL_BROWSER_MODE：在"+"或""之后不编码或解码字符，也不会删除""之后的尾随空格。 如果未指定此值，则对整个 URL 进行编码并删除尾随空格。

- ATL_URL_DECODE：在解析 URL 之前，将所有 %XX 序列转换为字符，包括转义序列。

- ATL_URL_ENCODE_PERCENT：对遇到的任何百分比符号进行编码。 默认情况下，百分比符号未编码。

- ATL_URL_ENCODE_SPACES_ONLY：仅对空格进行编码。

- ATL_URL_NO_ENCODE：不将不安全的字符转换为转义序列。

- ATL_URL_NO_META：不从 URL 中删除元序列（如"."和".."）。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

转换为规范形式涉及将不安全的字符和空格转换为转义序列。

## <a name="curlclear"></a><a name="clear"></a>Url：：清除

调用此方法以清除所有 URL 字段。

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>Url：：裂纹

调用此方法来解码和分析 URL。

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

*lpszUrl*<br/>
URL。

dwFlags**<br/>
指定ATL_URL_DECODE或ATL_URL_ESCAPE，用于在分析后将*lpszUrl*中的所有转义字符转换为其实际值。 （在 Visual C++ 2005 之前，ATL_URL_DECODE在分析之前转换了所有转义字符。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlcreateurl"></a><a name="createurl"></a>Url：：创建 Url

此方法从 CUrl 对象的组件字段构造 URL 字符串。

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>参数

*lpszUrl*<br/>
用于保存完整 URL 字符串的字符串缓冲区。

*pdwMax 长度*<br/>
*lpszUrl*字符串缓冲区的最大长度。

dwFlags**<br/>
指定ATL_URL_ESCAPE将*lpszUrl*中的所有转义字符转换为其实际值。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此方法附加其单个字段，以便使用以下格式构造完整的 URL 字符串：

**\<方案>：//\<用户>：\<通过>\@\<域>：\<端口>\<路径>\<额外的>**

调用此方法时 *，pdwMaxLength 参数*最初应包含*lpszUrl*参数引用的字符串缓冲区的最大长度。 *pdwMaxLength 参数*的值将随 URL 字符串的实际长度更新。

### <a name="example"></a>示例

此示例演示了创建 CUrl 对象并检索其 URL 字符串

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>Url：：CUrl

构造函数。

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>参数

*url*<br/>
要`CUrl`复制以创建 URL 的对象。

## <a name="curlcurl"></a><a name="dtor"></a>Url：_CUrl

析构函数。

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>Url：获取额外信息

调用此方法从 URL 获取额外信息（如*文本*或 +*文本*）。

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>返回值

返回包含额外信息的字符串。

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>Url：获取额外信息长度

调用此方法获取从 URL 检索的额外信息（如*文本*或 #*文本*）的长度。

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>返回值

返回包含额外信息的字符串的长度。

## <a name="curlgethostname"></a><a name="gethostname"></a>Url：获取主机名称

调用此方法从 URL 获取主机名。

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>返回值

返回主机名。

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>Url：获取主机名称长度

调用此方法以获取主机名的长度。

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>返回值

返回主机名长度。

## <a name="curlgetpassword"></a><a name="getpassword"></a>Url：获取密码

调用此方法从 URL 获取密码。

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>返回值

返回密码。

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>Url：获取密码长度

调用此方法获取密码的长度。

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>返回值

返回密码长度。

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>Url：获取端口号

调用此方法获取端口号。

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>返回值

返回端口号。

## <a name="curlgetscheme"></a><a name="getscheme"></a>Url：获取方案

调用此方法获取 URL 方案。

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>返回值

返回描述 URL 方案[的ATL_URL_SCHEME](atl-url-scheme-enum.md)值。

## <a name="curlgetschemename"></a><a name="getschemename"></a>Url：获取计划名称

调用此方法获取 URL 方案名称。

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>返回值

返回 URL 方案名称（如"http"或"ftp"）。

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>Url：获取方案名称长度

调用此方法获取 URL 方案名称的长度。

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>返回值

返回 URL 方案名称长度。

## <a name="curlgeturllength"></a><a name="geturllength"></a>Url：获取 Url 长度

调用此方法以获取 URL 长度。

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>返回值

返回 URL 长度。

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>Url：获取 UrlPath

调用此方法以获取 URL 路径。

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>返回值

返回 URL 路径。

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>Url：获取 Url 路径长度

调用此方法以获取 URL 路径长度。

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>返回值

返回 URL 路径长度。

## <a name="curlgetusername"></a><a name="getusername"></a>Url：获取用户名

调用此方法从 URL 获取用户名。

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>返回值

返回用户名。

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>Url：获取用户名长度

调用此方法以获取用户名的长度。

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>返回值

返回用户名长度。

## <a name="curloperator-"></a><a name="operator_eq"></a>Url：：运算符 |

将指定`CUrl`对象分配给当前`CUrl`对象。

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>参数

*url*<br/>
要`CUrl`复制到当前对象的对象。

### <a name="return-value"></a>返回值

返回对当前对象的引用。

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>Url：：设置额外信息

调用此方法以设置 URL 的额外信息（如*文本*或 #*文本*）。

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>参数

*lpszInfo*<br/>
包含要包含在 URL 中的额外信息的字符串。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlsethostname"></a><a name="sethostname"></a>Url：：设置主机名称

调用此方法以设置主机名。

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>参数

*lpszHost*<br/>
主机名。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlsetpassword"></a><a name="setpassword"></a>Url：：设置密码

调用此方法以设置密码。

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>参数

*lpszPass*<br/>
密码。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>Url：：设置端口号

调用此方法以设置端口号。

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>参数

*nPrt*<br/>
端口号。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlsetscheme"></a><a name="setscheme"></a>Url：：设置方案

调用此方法以设置 URL 方案。

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>参数

*nScheme*<br/>
方案[ATL_URL_SCHEME](atl-url-scheme-enum.md)值之一。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

您还可以按名称设置方案（请参阅[Url：：SetSchemeName）。](#setschemename)

## <a name="curlsetschemename"></a><a name="setschemename"></a>Url：：设置方案名称

调用此方法以设置 URL 方案名称。

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>参数

*lpszSchm*<br/>
URL 方案名称。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

您还可以使用[ATL_URL_SCHEME](atl-url-scheme-enum.md)常量来设置方案（请参阅[CUrl：：SetScheme）。](#setscheme)

## <a name="curlseturlpath"></a><a name="seturlpath"></a>Url：：设置 Url 路径

调用此方法以设置 URL 路径。

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
URL 路径。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="curlsetusername"></a><a name="setusername"></a>Url：：设置用户名

调用此方法以设置用户名。

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>参数

*lpszUser*<br/>
用户名。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="see-also"></a>另请参阅

[类](../../atl/reference/atl-classes.md)
