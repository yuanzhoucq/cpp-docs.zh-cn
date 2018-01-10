---
title: "CSettingsStoreSP 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs: C++
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cf9659b6c367146a565834bd65fdfc9f28a9812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 类
`CSettingsStoreSP`类是可用于创建的实例的帮助器类[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
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
  
|名称|描述|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|创建派生自的类的实例`CSettingsStore`。|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|设置运行时类。 `Create`方法使用运行时类来确定哪些对象创建的类。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|`m_dwUserData`|自定义用户数据存储在`CSettingsStoreSP`对象。 你提供的构造函数中的此数据`CSettingsStoreSP`对象。|  
|`m_pRegistry`|`CSettingsStore`-派生对象`Create`方法创建。|  
  
## <a name="remarks"></a>备注  
 你可以使用`CSettingsStoreSP`类将所有 MFC 注册表操作重定向到其他位置，如 XML 文件或数据库。 为此，请执行以下步骤：  
  
1.  创建一个类 (如`CMyStore`) 和从它派生`CSettingsStore`。  
  
2.  使用[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)宏与您的自定义`CSettingsStore`类，以启用动态创建。  
  
3.  重写虚函数并实现`Read`和`Write`你自定义的类中的函数。 实现任何其他功能来读取和写入所需的位置的数据。  
  
4.  在你的应用程序，调用`CSettingsStoreSP::SetRuntimeClass`，并传入一个指向[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)获取从您的类。  
  
 每当框架通常会访问注册表，它将现在动态实例化自定义类并使用它来读取或写入数据。  
  
 `CSettingsStoreSP::SetRuntimeClass`使用全局静态变量。 因此，一次只能有一个自定义存储是可用。  
  
## <a name="requirements"></a>惠?  
 **标头：** afxsettingsstore.h  
  
##  <a name="create"></a>CSettingsStoreSP::Create  
 创建派生自的对象的新实例[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAdmin`  
 布尔参数可确定是否`CSettingsStore`在管理员模式下创建对象。  
  
 [in] `bReadOnly`  
 布尔参数可确定是否`CSettingsStore`对象创建为只读访问权限。  
  
### <a name="return-value"></a>返回值  
 对新创建的引用`CSettingsStore`对象。  
  
### <a name="remarks"></a>备注  
 你可以使用方法[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)以确定哪种类型的对象`CSettingsStoreSP::Create`将创建。 默认情况下，此方法创建`CSettingsStore`对象。  
  
 如果你创建`CSettingsStore`对象在管理员模式下，所有注册表访问的默认位置为 HKEY_LOCAL_MACHINE。 否则，所有注册表访问的默认位置为 HKEY_CURRENT_USER。  
  
 如果`bAdmin`是`TRUE`，应用程序必须具有管理权限。 否则，它将它尝试访问注册表时失败。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`方法`CSettingsStoreSP`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP  
 构造[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)对象。  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwUserData`  
 用户定义的数据，`CSettingsStoreSP`对象存储。  
  
### <a name="remarks"></a>备注  
 `CSettingsStoreSP`对象将从数据存储`dwUserData`在受保护的成员变量`m_dwUserData`。  
  
##  <a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass  
 设置运行时类。 该方法[CSettingsStoreSP::Create](#create)运行时类用于确定要创建的对象类型。  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>参数  
 [in] `pRTI`  
 指向类的运行时类信息的指针派生自[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`如果通过标识类`pRTI`不派生自`CSettingsStore`。  
  
### <a name="remarks"></a>备注  
 你可以使用[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)派生的类`CSettingsStore`。 使用方法`SetRuntimeClass`如果你想要创建自定义类派生自的对象`CSettingsStore`。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)
