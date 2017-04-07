---
title: "CSettingsStoreSP 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP class
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 18
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 00131a3c03fdb2c1c1de247a8e1bdcfd9beaf852
ms.lasthandoff: 02/24/2017

---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 类
`CSettingsStoreSP`类是可用于创建实例的一个帮助器类[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|构造 `CSettingsStoreSP` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|创建派生自的类的实例`CSettingsStore`。|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|设置运行时类。 `Create`方法使用的运行时类来确定哪些类要创建的对象。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|`m_dwUserData`|自定义用户数据存储在`CSettingsStoreSP`对象。 你提供的构造函数中的此数据`CSettingsStoreSP`对象。|  
|`m_pRegistry`|`CSettingsStore`-派生对象`Create`方法创建。|  
  
## <a name="remarks"></a>备注  
 您可以使用`CSettingsStoreSP`类，以将所有 MFC 注册表操作重都定向到其他位置，如 XML 文件或数据库。 为此，请执行以下步骤：  
  
1.  创建一个类 (如`CMyStore`)，并获得从`CSettingsStore`。  
  
2.  使用[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)宏与您的自定义`CSettingsStore`类，以启用动态创建。  
  
3.  重写虚函数并实现`Read`和`Write`自定义类中的函数。 实现其他功能来对读取和写入数据所需的位置。  
  
4.  在应用程序中调用`CSettingsStoreSP::SetRuntimeClass`，并传入一个指向[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)获得从您的类。  
  
 每当框架通常会访问注册表，它将现在动态实例化自定义类并使用它来读取或写入数据。  
  
 `CSettingsStoreSP::SetRuntimeClass`使用全局静态变量。 因此，一次只能有一个自定义存储才可用。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxsettingsstore.h  
  
##  <a name="create"></a>CSettingsStoreSP::Create  
 创建派生自的对象的新实例[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAdmin`  
 一个布尔型参数，用于确定是否`CSettingsStore`在管理员模式下创建对象。  
  
 [in] `bReadOnly`  
 一个布尔型参数，用于确定是否`CSettingsStore`对象创建为只读访问权限。  
  
### <a name="return-value"></a>返回值  
 对新创建的引用`CSettingsStore`对象。  
  
### <a name="remarks"></a>备注  
 可以使用该方法[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)以确定哪种类型的对象`CSettingsStoreSP::Create`将创建。 默认情况下，此方法创建`CSettingsStore`对象。  
  
 如果您创建`CSettingsStore`对象在管理员模式下，所有注册表访问权限的默认位置为 HKEY_LOCAL_MACHINE。 否则，所有注册表访问权限的默认位置为 HKEY_CURRENT_USER。  
  
 如果`bAdmin`是`TRUE`，应用程序必须具有管理权限。 否则，它将失败时它将尝试访问注册表。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`方法`CSettingsStoreSP`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp 第&33;](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP  
 构造[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)对象。  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwUserData`  
 用户定义数据，`CSettingsStoreSP`对象存储区。  
  
### <a name="remarks"></a>备注  
 `CSettingsStoreSP`对象将从数据存储`dwUserData`在受保护的成员变量`m_dwUserData`。  
  
##  <a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass  
 设置运行时类。 该方法[CSettingsStoreSP::Create](#create)的运行时类用于确定要创建的对象类型。  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>参数  
 [in] `pRTI`  
 指向类的运行时类信息派生自[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`如果类由标识`pRTI`不源自`CSettingsStore`。  
  
### <a name="remarks"></a>备注  
 您可以使用[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)派生类从`CSettingsStore`。 使用方法`SetRuntimeClass`如果想要创建派生自的自定义类的对象`CSettingsStore`。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)

