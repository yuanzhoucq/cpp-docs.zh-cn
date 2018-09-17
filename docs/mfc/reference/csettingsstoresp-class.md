---
title: CSettingsStoreSP 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4223ce5c358f4e95ab94baac9d5cf0edda5ad73f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716332"
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
  
|名称|描述|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|创建派生自的类的实例`CSettingsStore`。|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|设置运行时类。 `Create`方法使用的运行时类来确定哪些类要创建的对象。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|`m_dwUserData`|自定义用户数据存储在`CSettingsStoreSP`对象。 提供的构造函数中的此数据`CSettingsStoreSP`对象。|  
|`m_pRegistry`|`CSettingsStore`-派生对象的`Create`方法创建。|  
  
## <a name="remarks"></a>备注  
 可以使用`CSettingsStoreSP`类，以将所有 MFC 注册表操作重都定向到其他位置，例如 XML 文件或数据库。 为此，请执行以下步骤：  
  
1.  创建一个类 (如`CMyStore`) 和从它派生`CSettingsStore`。  
  
2.  使用[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)并[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)与您的自定义的宏`CSettingsStore`类，以启用动态创建。  
  
3.  重写虚函数并实现`Read`和`Write`自定义类中的函数。 实现其他功能来读取和写入到所需位置的数据。  
  
4.  在应用程序中调用`CSettingsStoreSP::SetRuntimeClass`，然后将传入到指针[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)获取从您的类。  
  
 只要该框架通常会访问注册表，它将现在动态实例化自定义类并使用它来读取或写入数据。  
  
 `CSettingsStoreSP::SetRuntimeClass` 使用全局静态变量。 因此，一次只能有一个自定义存储才可用。  
  
## <a name="requirements"></a>要求  
 **标头：** afxsettingsstore.h  
  
##  <a name="create"></a>  CSettingsStoreSP::Create  
 创建一个派生自的对象的新实例[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>参数  
*bAdmin*<br/>
[in]一个布尔型参数，用于确定是否`CSettingsStore`在管理员模式下创建对象。  
  
*bReadOnly*<br/>
[in]一个布尔型参数，用于确定是否`CSettingsStore`对象创建的只读访问权限。  
  
### <a name="return-value"></a>返回值  
 对新创建的引用`CSettingsStore`对象。  
  
### <a name="remarks"></a>备注  
 可以使用方法[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)来确定哪种类型的对象`CSettingsStoreSP::Create`将创建。 默认情况下，此方法创建`CSettingsStore`对象。  
  
 如果您创建`CSettingsStore`对象在管理员模式下，所有注册表访问权限的默认位置为 HKEY_LOCAL_MACHINE。 否则，所有注册表访问权限的默认位置是 HKEY_CURRENT_USER。  
  
 如果*bAdmin*为 TRUE 时，应用程序必须具有管理权限。 否则，它将失败尝试访问注册表时。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`方法的`CSettingsStoreSP`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP  
 构造[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)对象。  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
*dwUserData*<br/>
[in]用户定义数据的`CSettingsStoreSP`对象存储。  
  
### <a name="remarks"></a>备注  
 `CSettingsStoreSP`对象存储中的数据*dwUserData*在受保护的成员变量`m_dwUserData`。  
  
##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass  
 设置运行时类。 该方法[CSettingsStoreSP::Create](#create)使用运行时类来确定要创建对象的类型。  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>参数  
*pRTI*<br/>
[in]指向类的运行时类信息的指针派生自[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 TRUE如果通过标识的类，则为 FALSE *pRTI*不派生自`CSettingsStore`。  
  
### <a name="remarks"></a>备注  
 可以使用[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)派生类从`CSettingsStore`。 使用方法`SetRuntimeClass`如果你想要创建自定义类派生自的对象`CSettingsStore`。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)
