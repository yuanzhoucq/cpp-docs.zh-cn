---
title: CTokenPrivileges 类
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: ceb9aeca6b99e7fc9d08625e11cbdb182fb3dc9e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330546"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 类

此类是结构的`TOKEN_PRIVILEGES`包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CTokenPrivileges
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CToken 特权：：CToken 特权](#ctokenprivileges)|构造函数。|
|[CToken 特权：：*CToken 特权](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToken 特权：：添加](#add)|向`CTokenPrivileges`对象添加一个或多个权限。|
|[CToken 特权：:Delete](#delete)|从`CTokenPrivileges`对象中删除权限。|
|[CToken 特权：:DeleteAll](#deleteall)|从`CTokenPrivileges`对象中删除所有权限。|
|[CToken 特权：：获取计数](#getcount)|返回`CTokenPrivileges`对象中的权限条目数。|
|[CToken 特权：：获取显示名称](#getdisplaynames)|检索对象中包含的特权的`CTokenPrivileges`显示名称。|
|[CToken 特权：获取长度](#getlength)|返回保存`TOKEN_PRIVILEGES``CTokenPrivileges`对象表示的结构所需的缓冲区大小（以字节为单位）。|
|[CToken 特权：：获取 Luids 和属性](#getluidsandattributes)|从`CTokenPrivileges`对象检索本地唯一标识符 （LUID） 和属性标志。|
|[CToken 特权：获取名称和属性](#getnamesandattributes)|从`CTokenPrivileges`对象检索特权名称和属性标志。|
|[CToken 特权：：GetPTOKEN_PRIVILEGES](#getptoken_privileges)|返回指向结构的`TOKEN_PRIVILEGES`指针。|
|[CToken 特权：：查找特权](#lookupprivilege)|检索与给定权限名称关联的属性。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CToken 特权：：运算符 TOKEN_PRIVILEGES |](#operator_const_token_privileges__star)|将值投射到指向结构的`TOKEN_PRIVILEGES`指针。|
|[CToken 特权：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是描述进程或线程的安全上下文并分配给登录到 Windows 系统的每个用户的对象。

访问令牌用于描述授予每个用户的各种安全特权。 特权由称为本地唯一标识符[（LUID](/windows/win32/api/winnt/ns-winnt-luid)） 的 64 位数字和描述符字符串组成。

类`CTokenPrivileges`是[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)结构的包装器，包含 0 或更多权限。 可以使用提供的类方法添加、删除或查询权限。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CToken 特权：：添加

向`CTokenPrivileges`访问令牌对象添加一个或多个权限。

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>参数

*psz特权*<br/>
指向 null 端接字符串的指针，该字符串指定在 WINNT 中定义的特权的名称。H 头文件。

*b 启用*<br/>
如果为 true，则启用该权限。 如果为 false，则禁用该特权。

*r特权*<br/>
对[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)结构的引用。 特权和属性从此结构复制并添加到`CTokenPrivileges`对象中。

### <a name="return-value"></a>返回值

如果成功添加权限，此方法的第一种形式将返回 true，否则为 false。

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CToken 特权：：CToken 特权

构造函数。

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`CTokenPrivileges`分配给新对象的对象。

*r特权*<br/>
要[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)分配给新`CTokenPrivileges`对象的TOKEN_PRIVILEGES结构。

### <a name="remarks"></a>备注

可以选择`CTokenPrivileges`使用`TOKEN_PRIVILEGES`结构或以前定义`CTokenPrivileges`的对象创建该对象。

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CToken 特权：：*CToken 特权

析构函数。

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有分配的资源。

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CToken 特权：:Delete

从`CTokenPrivileges`访问令牌对象中删除权限。

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>参数

*psz特权*<br/>
指向 null 端接字符串的指针，该字符串指定在 WINNT 中定义的特权的名称。H 头文件。 例如，此参数可以指定常量SE_SECURITY_NAME或其相应的字符串"SeSecurity特权"。

### <a name="return-value"></a>返回值

如果成功删除权限，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此方法可用作创建受限令牌的工具。

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CToken 特权：:DeleteAll

从`CTokenPrivileges`访问令牌对象中删除所有权限。

```
void DeleteAll() throw();
```

### <a name="remarks"></a>备注

删除`CTokenPrivileges`访问令牌对象中包含的所有权限。

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CToken 特权：：获取显示名称

检索访问令牌对象中包含的特权的`CTokenPrivileges`显示名称。

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>参数

*p 显示名称*<br/>
指向 `CString` 对象的数组的指针。 `CNames`定义为类型def： `CTokenPrivileges::CAtlArray<CString>`。

### <a name="remarks"></a>备注

参数`pDisplayNames`是指向对象数组的`CString`指针，该数组将接收与对象中包含的特权对应的`CTokenPrivileges`显示名称。 此方法仅检索 WINNT"定义权限"部分中指定的权限的显示名称。H。

此方法检索可显示的名称：例如，如果属性名称SE_REMOTE_SHUTDOWN_NAME，则可显示的名称为"从远程系统强制关闭"。 要获取系统名称，请使用[Ctoken 特权：：获取名称和属性](#getnamesandattributes)。

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CToken 特权：：获取计数

返回`CTokenPrivileges`对象中的权限条目数。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CTokenPrivileges`对象中包含的权限数。

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CToken 特权：获取长度

返回`CTokenPrivileges`对象的长度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回保存`TOKEN_PRIVILEGES``CTokenPrivileges`由对象表示的结构所需的字节数，包括它包含的所有特权条目。

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CToken 特权：：获取 Luids 和属性

从`CTokenPrivileges`对象检索本地唯一标识符 （LUID） 和属性标志。

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*p特权*<br/>
指向[LUID](/windows/win32/api/winnt/ns-winnt-luid)对象的数组。 `CLUIDArray`是定义为`CAtlArray<LUID> CLUIDArray`的类型def。

*pAttributes*<br/>
指向 DWORD 对象的数组。 如果省略此参数或 NULL，则不检索属性。 `CAttributes`是定义为`CAtlArray <DWORD> CAttributes`的类型def。

### <a name="remarks"></a>备注

此方法将枚举`CTokenPrivileges`访问令牌对象中包含的所有权限，并将单独的 LUID 和（可选）属性标志放入数组对象中。

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CToken 特权：获取名称和属性

从`CTokenPrivileges`对象检索名称和属性标志。

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*p名称*<br/>
指向对象数组的`CString`指针。 `CNames`是定义为`CAtlArray <CString> CNames`的类型def。

*pAttributes*<br/>
指向 DWORD 对象的数组。 如果省略此参数或 NULL，则不检索属性。 `CAttributes`是定义为`CAtlArray <DWORD> CAttributes`的类型def。

### <a name="remarks"></a>备注

此方法将枚举`CTokenPrivileges`对象中包含的所有权限，将名称和（可选）属性标志放入数组对象中。

此方法检索属性名称，而不是可显示的名称：例如，如果属性名称SE_REMOTE_SHUTDOWN_NAME，则系统名称为"SeRemote 关闭权限"。 要获取可显示名称，请使用方法[CToken 特权：：获取显示名称](#getdisplaynames)。

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CToken 特权：：GetPTOKEN_PRIVILEGES

返回指向结构的`TOKEN_PRIVILEGES`指针。

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)结构的指针。

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CToken 特权：：查找特权

检索与给定权限名称关联的属性。

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*psz特权*<br/>
指向 null 端接字符串的指针，该字符串指定在 WINNT 中定义的特权的名称。H 头文件。 例如，此参数可以指定常量SE_SECURITY_NAME或其相应的字符串"SeSecurity特权"。

*pdwAttributes*<br/>
指向接收属性的变量的指针。

### <a name="return-value"></a>返回值

如果成功检索属性，则返回 true，否则为 false。

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CToken 特权：：运算符 |

赋值运算符。

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>参数

*r特权*<br/>
要[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)分配给`CTokenPrivileges`对象的TOKEN_PRIVILEGES结构。

rhs**<br/>
要`CTokenPrivileges`分配给对象的对象。

### <a name="return-value"></a>返回值

返回更新`CTokenPrivileges`的对象。

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CToken 特权：：运算符 TOKEN_PRIVILEGES\*

将值投射到指向结构的`TOKEN_PRIVILEGES`指针。

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>备注

将值投射到指向[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)结构的指针。

## <a name="see-also"></a>另请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[卢ID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
