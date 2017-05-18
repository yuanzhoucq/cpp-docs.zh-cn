---
title: "CPrivateObjectSecurityDesc 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 154a4229f8963d3081e6e0518354d17968ee0e20
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 类
此类表示一个私有对象的安全描述符对象。  
  
## <a name="syntax"></a>语法  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|构造函数。|  
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|调用此方法将安全描述符和其访问控制列表 (Acl) 转换为支持的可继承的访问控制项 (Ace) 自动传播的格式。|  
|[CPrivateObjectSecurityDesc::Create](#create)|调用此方法来分配和初始化调用资源管理器创建的私有对象的自相关的安全描述符。|  
|[CPrivateObjectSecurityDesc::Get](#get)|调用此方法以从私有对象的安全描述符中检索信息。|  
|[CPrivateObjectSecurityDesc::Set](#set)|调用此方法来修改私有对象的安全描述符。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|赋值运算符。|  
  
## <a name="remarks"></a>备注  
 此类派生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，提供用于创建和管理私有对象的安全描述符的方法。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 调用此方法将安全描述符和其访问控制列表 (Acl) 转换为支持的可继承的访问控制项 (Ace) 自动传播的格式。  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象，用于引用该对象的父容器。 如果存在任何父容器，此参数为 NULL。  
  
 `ObjectType`  
 指向**GUID**结构，它标识与当前对象关联的对象类型。 设置`ObjectType`为 NULL，如果该对象不具有一个 GUID。  
  
 `bIsDirectoryObject`  
 指定新的对象是否可以包含其他对象。 如果值为 true 指示新对象是一个容器。 值为 false 指示新对象不是容器。  
  
 `GenericMapping`  
 指向[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)结构，它指定将对象的特定权限为每个泛型从右向的映射。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 此方法会尝试确定是否的 Ace 处于自由访问控制列表 (DACL) 和系统访问控制列表 (SACL) 的当前的安全描述符被继承自父安全描述符。 它将调用[ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403)函数。  
  
##  <a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 构造函数。  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化`CPrivateObjectSecurityDesc`对象。  
  
##  <a name="dtor"></a>CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc  
 析构函数。  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放所有已分配的资源并删除该专有对象安全描述符。  
  
##  <a name="create"></a>CPrivateObjectSecurityDesc::Create  
 调用此方法来分配和初始化调用资源管理器创建的私有对象的自相关的安全描述符。  
  
```
bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象，用于引用在其中创建新对象的父目录。 如果没有父目录，设置为 NULL。  
  
 `pCreator`  
 指向对象的创建者提供的安全描述符的指针。 如果对象的创建者不显式传递为新的对象的安全信息，请将此参数设置为 NULL。  
  
 `bIsDirectoryObject`  
 指定新的对象是否可以包含其他对象。 如果值为 true 指示新对象是一个容器。 值为 false 指示新对象不是容器。  
  
 `Token`  
 引用[CAccessToken](../../atl/reference/caccesstoken-class.md)名义创建对象的客户端进程对象。  
  
 `GenericMapping`  
 指向[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)结构，它指定将对象的特定权限为每个泛型从右向的映射。  
  
 `ObjectType`  
 指向**GUID**结构，它标识与当前对象关联的对象类型。 设置`ObjectType`为 NULL，如果该对象不具有一个 GUID。  
  
 *bIsContainerObject*  
 指定新的对象是否可以包含其他对象。 如果值为 true 指示新对象是一个容器。 值为 false 指示新对象不是容器。  
  
 `AutoInheritFlags`  
 一组位标志，用于控制如何将访问控制项 (Ace) 继承从`pParent`。 请参阅[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)的更多详细信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 此方法调用[CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405)或[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)。  
  
 第二种方法，它可用于指定新的对象的对象类型的 GUID 或控制如何继承 Ace，仅适用于运行 Windows 2000 的系统及更高版本。  
  
> [!NOTE]
>  自相关的安全描述符是将其所有的安全信息存储在连续内存块的安全描述符。  
  
##  <a name="get"></a>CPrivateObjectSecurityDesc::Get  
 调用此方法以从私有对象的安全描述符中检索信息。  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>参数  
 `si`  
 一组位标志，用于指示要检索的安全描述符的部分。 此值可以是组合的[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位标志。  
  
 `pResult`  
 指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)接收所请求信息的副本从指定的安全描述符的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 安全描述符是结构和关联的数据，其中包含可保护对象的安全信息。  
  
##  <a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =  
 赋值运算符。  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rhs`  
 `CPrivateObjectSecurityDesc`要分配给当前对象。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CPrivateObjectSecurityDesc`对象。  
  
##  <a name="set"></a>CPrivateObjectSecurityDesc::Set  
 调用此方法来修改私有对象的安全描述符。  
  
```
bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```  
  
### <a name="parameters"></a>参数  
 `si`  
 一组位标志，用于指示要设置的安全描述符的部分。 此值可以是组合的[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位标志。  
  
 *修改*  
 指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)对象。 此安全描述符的部分由`si`参数应用于对象的安全描述符。  
  
 `GenericMapping`  
 指向[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)结构，它指定将对象的特定权限为每个泛型从右向的映射。  
  
 `Token`  
 引用[CAccessToken](../../atl/reference/caccesstoken-class.md)名义创建对象的客户端进程对象。  
  
 `AutoInheritFlags`  
 一组位标志，用于控制如何将访问控制项 (Ace) 继承从`pParent`。 请参阅[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)的更多详细信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 true；如果失败，则返回 false。  
  
### <a name="remarks"></a>备注  
 第二种方法，它可用于指定对象的对象类型的 GUID 或控制如何继承 Ace，仅适用于运行 Windows 2000 的系统及更高版本。  
  
## <a name="see-also"></a>另请参阅  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全的全局函数](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc 类](../../atl/reference/csecuritydesc-class.md)

