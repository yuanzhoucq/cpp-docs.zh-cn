---
title: "CTokenGroups 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CTokenGroups
- ATL.CTokenGroups
- CTokenGroups
dev_langs:
- C++
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 41b93e1c0a2e55013e280023a7f47610d38ddc10
ms.lasthandoff: 02/24/2017

---
# <a name="ctokengroups-class"></a>CTokenGroups 类
此类是包装器**TOKEN_GROUPS**结构。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CTokenGroups
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTokenGroups::CTokenGroups](#ctokengroups)|构造函数。|  
|[CTokenGroups:: ~ CTokenGroups](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTokenGroups::Add](#add)|添加`CSid`或现有**TOKEN_GROUPS**结构`CTokenGroups`对象。|  
|[CTokenGroups::Delete](#delete)|删除`CSid`从及其关联属性`CTokenGroups`对象。|  
|[CTokenGroups::DeleteAll](#deleteall)|将删除所有`CSid`对象和从其关联的属性`CTokenGroups`对象。|  
|[CTokenGroups::GetCount](#getcount)|返回数`CSid`对象和关联的属性中包含**CTokenGroups**对象。|  
|[CTokenGroups::GetLength](#getlength)|返回的大小`CTokenGroups`对象。|  
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|检索一个指向**TOKEN_GROUPS**结构。|  
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|检索`CSid`对象和属性属于`CTokenGroups`对象。|  
|[CTokenGroups::LookupSid](#lookupsid)|检索与关联的特性`CSid`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|强制转换`CTokenGroups`对象的指针到**TOKEN_GROUPS**结构。|  
|[CTokenGroups::operator =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一个对象，描述进程或线程的安全上下文，并分配给每个用户登录到 Windows NT 或 Windows 2000 的系统。  
  
 **CTokenGroups**类是包装器[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)包含访问令牌中的组安全标识符 (Sid) 信息的结构。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="a-nameadda--ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Add  
 添加`CSid`或现有**TOKEN_GROUPS**结构`CTokenGroups`对象。  
  
```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );  
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 一个[CSid](../../atl/reference/csid-class.md)对象。  
  
 `dwAttributes`  
 要将与相关联的特性`CSid`对象。  
  
 *rTokenGroups*  
 一个[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)结构。  
  
### <a name="remarks"></a>备注  
 这些方法将添加一个或多个`CSid`对象和为其关联的属性`CTokenGroups`对象。  
  
##  <a name="a-namectokengroupsa--ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups  
 构造函数。  
  
```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );  
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CTokenGroups`对象或[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)结构用来构造`CTokenGroups`对象。  
  
### <a name="remarks"></a>备注  
 `CTokenGroups` （可选） 可以使用创建对象**TOKEN_GROUPS**结构或以前定义`CTokenGroups`对象。  
  
##  <a name="a-namedtora--ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups:: ~ CTokenGroups  
 析构函数。  
  
```
virtual ~CTokenGroups() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源。  
  
##  <a name="a-namedeletea--ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete  
 删除`CSid`从及其关联属性`CTokenGroups`对象。  
  
```
bool Delete(const CSid& rSid) throw();
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md)为其安全标识符 (SID) 和属性应删除的对象。  
  
### <a name="return-value"></a>返回值  
 返回 true if`CSid`被删除，则返回 false 否则。  
  
##  <a name="a-namedeletealla--ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll  
 将删除所有`CSid`对象和从其关联的属性`CTokenGroups`对象。  
  
```
void DeleteAll() throw();
```  
  
##  <a name="a-namegetcounta--ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount  
 返回数`CSid`中所含对象`CTokenGroups`。  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回数[CSid](../../atl/reference/csid-class.md)对象和包含在其关联的属性`CTokenGroups`对象。  
  
##  <a name="a-namegetlengtha--ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength  
 返回的大小**CTokenGroup**对象。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="remarks"></a>备注  
 返回的总大小**CTokenGroup**对象，以字节为单位。  
  
##  <a name="a-namegetptokengroupsa--ctokengroupsgetptokengroups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS  
 检索一个指向**TOKEN_GROUPS**结构。  
  
```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```  
  
### <a name="return-value"></a>返回值  
 检索一个指向[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)结构属于`CTokenGroups`访问令牌的对象。  
  
##  <a name="a-namegetsidsandattributesa--ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes  
 检索`CSid`对象以及 （可选） 的属性属于`CTokenGroups`对象。  
  
```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>参数  
 `pSids`  
 指向数组的指针[CSid](../../atl/reference/csid-class.md)对象。  
  
 `pAttributes`  
 指向 dword 值的数组的指针。 如果此参数被省略或为 NULL，将不会检索属性。  
  
### <a name="remarks"></a>备注  
 此方法将枚举所有`CSid`中所含对象`CTokenGroups`对象，并将它们和 （可选） 的特性标志放入数组对象。  
  
##  <a name="a-namelookupsida--ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::LookupSid  
 检索与关联的特性`CSid`对象。  
  
```
bool LookupSid(  
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```  
  
### <a name="parameters"></a>参数  
 `rSid`  
 [CSid](../../atl/reference/csid-class.md)对象。  
  
 `pdwAttributes`  
 指向一个 dword 值，它将接受`CSid`对象的属性。 如果省略或为 NULL，将不会检索该属性。  
  
### <a name="return-value"></a>返回值  
 返回 true if`CSid`找到，则 false 否则。  
  
### <a name="remarks"></a>备注  
 设置`pdwAttributes`到 NULL 提供了一种确认是否存在`CSid`而无需访问该属性。 请注意，此方法应不使用时不正确的结果可能会出现在 Windows 2000 下检查访问权限。 应用程序应改用[CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。  
  
##  <a name="a-nameoperatoreqa--ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::operator =  
 赋值运算符。  
  
```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);  
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CTokenGroups`对象或[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)结构要分配给`CTokenGroups`对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CTokenGroups`对象。  
  
##  <a name="a-nameoperatorconsttokengroupsstara--ctokengroupsoperator-const-tokengroups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *  
 将为指针值强制转换**TOKEN_GROUPS**结构。  
  
```  
operator const TOKEN_GROUPS *() const throw(...);
```  
  
### <a name="remarks"></a>备注  
 将为指针值强制转换[TOKEN_GROUPS](http://msdn.microsoft.com/library/windows/desktop/aa379624)结构。  
  
## <a name="see-also"></a>另请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [CSid 类](../../atl/reference/csid-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)

