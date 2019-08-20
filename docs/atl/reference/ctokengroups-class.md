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
ms.openlocfilehash: 4e5d06ca01201bf415afedbe6f6e5bca096f68fa
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915579"
---
# <a name="ctokengroups-class"></a>CTokenGroups 类

此类是`TOKEN_GROUPS`结构的包装器。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CTokenGroups
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|构造函数。|
|[CTokenGroups::~CTokenGroups](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTokenGroups::Add](#add)|向对象添加`TOKEN_GROUPS`或现有结构 `CSid` `CTokenGroups` 。|
|[CTokenGroups::Delete](#delete)|从对象中删除`CSid` `CTokenGroups`及其关联特性。|
|[CTokenGroups::DeleteAll](#deleteall)|从对象中删除所有`CSid`对象及其关联的属性。 `CTokenGroups`|
|[CTokenGroups::GetCount](#getcount)|返回`CSid` 对象`CTokenGroups`中包含的对象数和关联属性。|
|[CTokenGroups::GetLength](#getlength)|返回`CTokenGroups`对象的大小。|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|检索指向`TOKEN_GROUPS`结构的指针。|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|检索属于`CSid` `CTokenGroups`对象的对象和属性。|
|[CTokenGroups::LookupSid](#lookupsid)|检索与`CSid`对象相关联的属性。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|将对象强制转换为指向`TOKEN_GROUPS`结构的指针。 `CTokenGroups`|
|[CTokenGroups:: operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

[访问令牌](/windows/desktop/SecAuthZ/access-tokens)是一个对象, 该对象描述进程或线程的安全上下文, 并分配给登录到 Windows 系统的每个用户。

类是 [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) 结构的包装, 其中包含有关访问令牌中的组安全标识符 (sid) 的信息。`CTokenGroups`

有关 Windows 中的访问控制模型的简介, 请参阅 Windows SDK 中的[访问控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="requirements"></a>要求

**标头:** atlsecurity。h

##  <a name="add"></a>CTokenGroups:: Add

向对象添加`TOKEN_GROUPS`或现有结构 `CSid` `CTokenGroups` 。

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)对象。

*dwAttributes*<br/>
要与`CSid`对象关联的特性。

*rTokenGroups*<br/>
[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)结构。

### <a name="remarks"></a>备注

这些方法将一个或多`CSid`个对象及其关联特性添加`CTokenGroups`到对象。

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

构造函数。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
用于构造`CTokenGroups`对象的对象或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)`CTokenGroups`结构。

### <a name="remarks"></a>备注

可以`CTokenGroups`选择`TOKEN_GROUPS`使用结构或以前定义`CTokenGroups`的对象来创建对象。

##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups

析构函数。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有已分配的资源。

##  <a name="delete"></a>  CTokenGroups::Delete

从对象中删除`CSid` `CTokenGroups`及其关联特性。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>参数

*rSid*<br/>
应为其移除安全标识符 (SID) 和特性的[CSid](../../atl/reference/csid-class.md)对象。

### <a name="return-value"></a>返回值

如果`CSid`已移除, 则返回 true, 否则返回 false。

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

从对象中删除所有`CSid`对象及其关联的属性。 `CTokenGroups`

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

返回中`CSid` `CTokenGroups`包含的对象数。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回`CTokenGroups`对象中包含的[CSid](../../atl/reference/csid-class.md)对象及其关联属性的数目。

##  <a name="getlength"></a>  CTokenGroups::GetLength

返回`CTokenGroup`对象的大小。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>备注

返回`CTokenGroup`对象的总大小 (以字节为单位)。

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

检索指向`TOKEN_GROUPS`结构的指针。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>返回值

检索指向属于`CTokenGroups`访问令牌对象的[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)结构的指针。

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

检索对象和 (可选) 属于`CTokenGroups`对象的特性。 `CSid`

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSids*<br/>
指向[CSid](../../atl/reference/csid-class.md)对象的数组的指针。

*pAttributes*<br/>
指向 Dword 数组的指针。 如果省略此参数或为 NULL, 则不检索特性。

### <a name="remarks"></a>备注

此方法将枚举`CSid` `CTokenGroups`对象中包含的所有对象, 并将这些对象和 (可选) 属性标志放入数组对象。

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

检索与`CSid`对象相关联的属性。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>参数

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)对象。

*pdwAttributes*<br/>
一个指向 DWORD 的指针, 它将`CSid`接受对象的特性。 如果省略或为 NULL, 则不会检索特性。

### <a name="return-value"></a>返回值

如果`CSid`找到, 则返回 true, 否则返回 false。

### <a name="remarks"></a>备注

将*pdwAttributes*设置为 NULL 可提供一种在`CSid`不访问属性的情况下确认是否存在的方法。 请注意, 此方法不应用于检查访问权限。 应用程序应改为使用[CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

##  <a name="operator_eq"></a>CTokenGroups:: operator =

赋值运算符。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>参数

rhs<br/>
要分配给[对象的](/windows/desktop/api/winnt/ns-winnt-token_groups) `CTokenGroups` 对象或TOKEN_GROUPS结构。`CTokenGroups`

### <a name="return-value"></a>返回值

返回已更新`CTokenGroups`的对象。

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: operator const TOKEN_GROUPS *

将值强制转换为指向`TOKEN_GROUPS`结构的指针。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>备注

将一个值转换为指向[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)结构的指针。

## <a name="see-also"></a>请参阅

[安全示例](../../overview/visual-cpp-samples.md)<br/>
[CSid 类](../../atl/reference/csid-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
