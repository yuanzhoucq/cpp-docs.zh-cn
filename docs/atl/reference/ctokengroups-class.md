---
title: CTokenGroups 类
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: ccfa628f4a099f7e13eb09d272c72c2bdd846f37
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746389"
---
# <a name="ctokengroups-class"></a>CTokenGroups 类

此类是结构的`TOKEN_GROUPS`包装器。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CTokenGroups
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CToken 组：CToken 组](#ctokengroups)|构造函数。|
|[CToken 组：*CToken 组](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToken 组：：添加](#add)|将`CSid`或现有`TOKEN_GROUPS`结构添加到`CTokenGroups`对象。|
|[CToken组：:Delete](#delete)|从`CTokenGroups`对象中删除`CSid`a 及其关联的属性。|
|[CToken组：:DeleteAll](#deleteall)|从`CTokenGroups`对象中删除`CSid`所有对象及其关联属性。|
|[CToken 组：获取计数](#getcount)|返回对象中包含的`CSid`对象和关联属性的数量`CTokenGroups`。|
|[CToken 组：获取长度](#getlength)|返回`CTokenGroups`对象的大小。|
|[CToken 组：：GetPTOKEN_GROUPS](#getptoken_groups)|检索指向结构的`TOKEN_GROUPS`指针。|
|[Ctoken 组：：获取 Sids 和属性](#getsidsandattributes)|检索属于`CSid``CTokenGroups`对象的对象和属性。|
|[CToken 组：：查找Sid](#lookupsid)|检索与`CSid`对象关联的属性。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CToken组：：操作员TOKEN_GROUPS |](#operator_const_token_groups__star)|将`CTokenGroups`对象强制转换为指向结构的`TOKEN_GROUPS`指针。|
|[CToken组：：运算符 |](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

[访问令牌](/windows/win32/SecAuthZ/access-tokens)是描述进程或线程的安全上下文并分配给登录到 Windows 系统的每个用户的对象。

类`CTokenGroups`是[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)结构的包装器，包含有关访问令牌中的组安全标识符 （SID） 的信息。

有关 Windows 中访问控制模型的简介，请参阅 Windows SDK 中[的访问控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标题：** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CToken 组：：添加

将`CSid`或现有`TOKEN_GROUPS`结构添加到`CTokenGroups`对象。

```cpp
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)对象。

*dwAttributes*<br/>
要与`CSid`对象关联的属性。

*rToken组*<br/>
[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)结构。

### <a name="remarks"></a>备注

这些方法向`CTokenGroups`对象添加一个或多个`CSid`对象及其关联属性。

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CToken 组：CToken 组

构造函数。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`CTokenGroups`用来[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)构造`CTokenGroups`对象的对象或TOKEN_GROUPS结构。

### <a name="remarks"></a>备注

可以选择`CTokenGroups`使用`TOKEN_GROUPS`结构或以前定义`CTokenGroups`的对象创建该对象。

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CToken 组：*CToken 组

析构函数。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有分配的资源。

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CToken组：:Delete

从`CTokenGroups`对象中删除`CSid`a 及其关联的属性。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>参数

*rSid*<br/>
应为其删除安全标识符 （SID） 和属性的[CSid](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果删除 ，`CSid`则返回 true，否则为 false。

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CToken组：:DeleteAll

从`CTokenGroups`对象中删除`CSid`所有对象及其关联属性。

```cpp
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CToken 组：获取计数

返回 中包含的`CSid``CTokenGroups`对象数。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回对象中包含的[CSid](../../atl/reference/csid-class.md)对象及其关联属性的数量`CTokenGroups`。

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CToken 组：获取长度

返回`CTokenGroup`对象的大小。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>备注

返回`CTokenGroup`对象的总大小（以字节为单位）。

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CToken 组：：GetPTOKEN_GROUPS

检索指向结构的`TOKEN_GROUPS`指针。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>返回值

检索指向属于访问令牌对象的[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)结构的`CTokenGroups`指针。

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>Ctoken 组：：获取 Sids 和属性

检索`CSid`对象和（可选）属于`CTokenGroups`该对象的属性。

```cpp
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSids*<br/>
指向[CSid](../../atl/reference/csid-class.md)对象的数组。

*pAttributes*<br/>
指向 DORD 数组的指针。 如果省略此参数或 NULL，则不检索属性。

### <a name="remarks"></a>备注

此方法将枚举`CSid``CTokenGroups`对象中包含的所有对象并将其放置，并（有选择地）将属性标志放入数组对象中。

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CToken 组：：查找Sid

检索与`CSid`对象关联的属性。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)对象。

*pdwAttributes*<br/>
指向将接受`CSid`对象的属性的 DWORD 的指针。 如果省略或 NULL，将不会检索该属性。

### <a name="return-value"></a>返回值

如果找到 ，`CSid`则返回 true，否则为 false。

### <a name="remarks"></a>备注

将*pdwAttributes*设置为 NULL 提供了一种`CSid`在不访问属性的情况下确认 是否存在的方法。 请注意，此方法不应用于检查访问权限。 相反，应用程序应使用[CAccessToken：：检查令牌成员资格](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CToken组：：运算符 |

赋值运算符。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs**<br/>
要`CTokenGroups`分配给`CTokenGroups`对象的对象或[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)结构。

### <a name="return-value"></a>返回值

返回更新`CTokenGroups`的对象。

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CToken组：：操作员TOKEN_GROUPS |

将值投射到指向结构的`TOKEN_GROUPS`指针。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>备注

将值投射到指向[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)结构的指针。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[CSid 类](../../atl/reference/csid-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局功能](../../atl/reference/security-global-functions.md)
