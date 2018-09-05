---
title: CTokenGroups 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87109793625435945c45b2643ccd674946acff49
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752640"
---
# <a name="ctokengroups-class"></a>CTokenGroups 类

此类是包装`TOKEN_GROUPS`结构。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
|[CTokenGroups::Add](#add)|将添加`CSid`的或现有的`TOKEN_GROUPS`结构`CTokenGroups`对象。|
|[CTokenGroups::Delete](#delete)|删除`CSid`及其关联属性从`CTokenGroups`对象。|
|[CTokenGroups::DeleteAll](#deleteall)|将删除所有`CSid`对象和从其关联的属性`CTokenGroups`对象。|
|[CTokenGroups::GetCount](#getcount)|返回的数`CSid`对象和关联的属性中包含`CTokenGroups`对象。|
|[CTokenGroups::GetLength](#getlength)|返回的大小`CTokenGroups`对象。|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|检索指向的`TOKEN_GROUPS`结构。|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|检索`CSid`对象和属性属于`CTokenGroups`对象。|
|[CTokenGroups::LookupSid](#lookupsid)|检索与关联的特性`CSid`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|强制转换`CTokenGroups`指向的对象`TOKEN_GROUPS`结构。|
|[CTokenGroups::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

[访问令牌](/windows/desktop/SecAuthZ/access-tokens)是一个对象，用于描述进程或线程的安全上下文并分配给每个用户登录到 Windows 系统。

`CTokenGroups`类是包装[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构，其中包含访问令牌中的组安全标识符 (Sid) 有关的信息。

有关 Windows 中的访问控制模型的简介，请参阅[访问控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>要求

**标头：** atlsecurity.h

##  <a name="add"></a>  CTokenGroups::Add

将添加`CSid`的或现有的`TOKEN_GROUPS`结构`CTokenGroups`对象。

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>参数

*rSid*  
一个[CSid](../../atl/reference/csid-class.md)对象。

*dwAttributes*  
要将与相关联的特性`CSid`对象。

*rTokenGroups*  
一个[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构。

### <a name="remarks"></a>备注

这些方法将添加一个或多个`CSid`对象和其关联的属性到`CTokenGroups`对象。

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

构造函数。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*  
`CTokenGroups`对象或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构用来构造`CTokenGroups`对象。

### <a name="remarks"></a>备注

`CTokenGroups` （可选） 可以使用创建对象`TOKEN_GROUPS`结构或以前定义`CTokenGroups`对象。

##  <a name="dtor"></a>  CTokenGroups:: ~ CTokenGroups

析构函数。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>备注

析构函数释放所有已分配的资源。

##  <a name="delete"></a>  CTokenGroups::Delete

删除`CSid`及其关联属性从`CTokenGroups`对象。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>参数

*rSid*  
[CSid](../../atl/reference/csid-class.md)为其安全标识符 (SID) 和属性应删除的对象。

### <a name="return-value"></a>返回值

返回 true 如果`CSid`被删除，则返回 false 否则。

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

将删除所有`CSid`对象和从其关联的属性`CTokenGroups`对象。

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

返回的数`CSid`中所含对象`CTokenGroups`。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回的数[CSid](../../atl/reference/csid-class.md)对象和其关联的属性中包含`CTokenGroups`对象。

##  <a name="getlength"></a>  CTokenGroups::GetLength

返回的大小`CTokenGroup`对象。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>备注

返回的总大小`CTokenGroup`对象，以字节为单位。

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

检索指向的`TOKEN_GROUPS`结构。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>返回值

检索一个指向[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构属于`CTokenGroups`访问令牌的对象。

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

检索`CSid`对象和 （可选） 的属性属于`CTokenGroups`对象。

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>参数

*pSids*  
指向数组的指针[CSid](../../atl/reference/csid-class.md)对象。

*pAttributes*  
指向 dword 值的数组的指针。 如果省略或为 NULL，此参数，不会检索属性。

### <a name="remarks"></a>备注

此方法将枚举的所有`CSid`中所含对象`CTokenGroups`对象，并将它们和 （可选） 的特性标志放入数组对象。

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

检索与关联的特性`CSid`对象。

```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>参数

*rSid*  
[CSid](../../atl/reference/csid-class.md)对象。

*pdwAttributes*  
指向一个 dword 值，将接受`CSid`对象的属性。 如果省略或为 NULL，将不会检索该属性。

### <a name="return-value"></a>返回值

返回 true 如果`CSid`找到，则 false 否则。

### <a name="remarks"></a>备注

设置*pdwAttributes*到 NULL 提供一种确认是否存在`CSid`而无需访问该属性。 请注意，此方法应不使用检查访问权限。 应用程序应改用[CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

##  <a name="operator_eq"></a>  CTokenGroups::operator =

赋值运算符。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>参数

*rhs*  
`CTokenGroups`对象或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构，以将分配给`CTokenGroups`对象。

### <a name="return-value"></a>返回值

返回已更新`CTokenGroups`对象。

##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator const TOKEN_GROUPS *

将值转换为一个指向`TOKEN_GROUPS`结构。

```  
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>备注

将值转换为一个指向[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)结构。

## <a name="see-also"></a>请参阅

[安全示例](../../visual-cpp-samples.md)   
[CSid 类](../../atl/reference/csid-class.md)   
[类概述](../../atl/atl-class-overview.md)   
[安全全局函数](../../atl/reference/security-global-functions.md)
