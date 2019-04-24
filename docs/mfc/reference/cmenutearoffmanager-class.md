---
title: CMenuTearOffManager 类
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: 8b92ddad9d3a6de41cf6914dee268f6e54b5d420
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163703"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 类

管理可拖曳菜单。 可拖曳菜单是菜单栏上的菜单。 用户可以从菜单栏移开可拖曳菜单，从而使可拖拽菜单浮动。

   有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|构造 `CMenuTearOffManager` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
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

下面的示例演示如何构造和初始化`CMenuTearOffManager`对象通过调用`CWinAppEX::EnableTearOffMenus`方法。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>要求

**标头：** afxmenutearoffmanager.h

##  <a name="build"></a>  CMenuTearOffManager::Build

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>参数

[in] *uiTearOffBarID*<br/>

[in] *strText*<br/>

### <a name="remarks"></a>备注

##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager

构造[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。

```
CMenuTearOffManager();
```

### <a name="remarks"></a>备注

在大多数情况下，不应创建`CMenuTearOffManager`手动。 你的应用程序框架创建`CMenuTearOffManager`对象在调用时[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。

##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="initialize"></a>  CMenuTearOffManager::Initialize

初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>参数

*lpszRegEntry*<br/>
[in]一个字符串，包含注册表项的路径。 您的应用程序在此注册表项中存储的分离式条形图的设置。

*uiTearOffMenuFirst*<br/>
[in]分离式菜单第一个菜单 ID。

*uiTearOffMenuLast*<br/>
[in]分离式菜单最后一个菜单 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从菜单 Id 的范围*uiTearOffMenuFirst*到*uiTearOffMenuLast*必须是连续的时间间隔。 间隔用于定义可以出现在应用程序中同时拖曳菜单数。

##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>参数

[in] *uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="parse"></a>  CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>参数

[in] *str*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="reset"></a>  CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>参数

[in]*hmenu*<br/>

### <a name="remarks"></a>备注

##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>参数

[in] *uiCmdId*<br/>

[in] *bUse*<br/>

### <a name="remarks"></a>备注

##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>参数

[in] *hMenu*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
