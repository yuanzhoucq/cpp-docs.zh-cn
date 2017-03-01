---
title: "CMenuTearOffManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenuTearOffManager
dev_langs:
- C++
helpviewer_keywords:
- CMenuTearOffManager class
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: 31
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
ms.openlocfilehash: 53677bbea54e428e5f080f5c1f73c576abcf99a5
ms.lasthandoff: 02/24/2017

---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 类
管理可拖曳菜单。 可拖曳菜单是菜单栏上的菜单。 用户可以从菜单栏移开可拖曳菜单，从而使可拖拽菜单浮动。  
  
## <a name="syntax"></a>语法  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|构造 `CMenuTearOffManager` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|初始化`CMenuTearOffManager`对象。|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>备注  
 为了在您的应用程序中使用拖曳菜单，您必须具有`CMenuTearOffManager`对象。 在大多数情况下，不会创建或初始化`CMenuTearOffManager`直接对象。 这在调用时为您处理[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)函数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造和初始化`CMenuTearOffManager`对象通过调用`CWinAppEX::EnableTearOffMenus`方法。 此代码段属于[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&12;](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>要求  
 **标头︰** afxmenutearoffmanager.h  
  
##  <a name="a-namebuilda--cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearOffManager::Build  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiTearOffBarID`  
 [in] `strText`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecmenutearoffmanagera--cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager  
 构造[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，不应创建`CMenuTearOffManager`手动。 您的应用程序框架创建`CMenuTearOffManager`对象在调用时[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。  
  
##  <a name="a-namegetregpatha--cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearOffManager::GetRegPath  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameinitializea--cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Initialize  
 初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszRegEntry`  
 一个字符串，包含路径的注册表项。 您的应用程序在此注册表项中存储的分开的条形图的设置。  
  
 [in] `uiTearOffMenuFirst`  
 可拖曳菜单第一个菜单 ID。  
  
 [in] `uiTearOffMenuLast`  
 最后一个可拖曳菜单的菜单 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从菜单 Id 的范围`uiTearOffMenuFirst`到`uiTearOffMenuLast`必须是连续的时间间隔。 在间隔定义可以出现在应用程序中的同一时间可拖曳菜单数。  
  
##  <a name="a-nameisdynamicida--cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameparsea--cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `str`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namereseta--cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearOffManager::Reset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `hmenu`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetinusea--cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenuTearOffManager::SetInUse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdId`  
 [in] `bUse`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetuptearoffmenusa--cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `hMenu`  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)

