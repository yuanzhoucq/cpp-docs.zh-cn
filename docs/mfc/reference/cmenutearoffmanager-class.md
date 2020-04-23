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
ms.openlocfilehash: 6aef644cb7364184df91a6e8caee18cac65af4cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751806"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 类

管理可拖曳菜单。 可拖曳菜单是菜单栏上的菜单。 用户可以从菜单栏移开可拖曳菜单，从而使可拖拽菜单浮动。

   有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMenuTearoff 管理器：：CMenutearoff 管理器](#cmenutearoffmanager)|构造 `CMenuTearOffManager` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMenuTearoff 管理器：：生成](#build)||
|[CMenuTearoff 经理：获取 RegPath](#getregpath)||
|[CMenuTearoff 管理器：初始化](#initialize)|初始化`CMenuTearOffManager`对象。|
|[CMenutearoff 管理器：：动态 ID](#isdynamicid)||
|[CMenuTearoff 经理：:P](#parse)||
|[CMenuTearoff 管理器：重置](#reset)||
|[CMenutearoff 管理器：：Setinuse](#setinuse)||
|[CMenuTearoff 管理器：：设置"关闭菜单"](#setuptearoffmenus)||

## <a name="remarks"></a>备注

为了在应用程序中使用分泪菜单，您必须有一个`CMenuTearOffManager`对象。 在大多数情况下，不会直接创建或初始化`CMenuTearOffManager`对象。 当您调用[CWinAppEx：：启用TearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)函数时，将为您处理此操作。

## <a name="example"></a>示例

下面的示例演示如何通过调用`CMenuTearOffManager``CWinAppEX::EnableTearOffMenus`方法构造和初始化对象。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>要求

**标题：** afxmenutearoff 管理器.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearoff 管理器：：生成

```cpp
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>参数

[在]*乌伊蒂尔·乌夫巴里德*<br/>

[在]*斯特文本*<br/>

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearoff 管理器：：CMenutearoff 管理器

构造[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)对象。

```
CMenuTearOffManager();
```

### <a name="remarks"></a>备注

在大多数情况下，不应手动创建。 `CMenuTearOffManager` 当您调用 CWinAppEx`CMenuTearOffManager`时，应用程序的框架将创建对象[：：启用TearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearoff 经理：获取 RegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearoff 管理器：初始化

初始化[CMenuTearOff 管理器](../../mfc/reference/cmenutearoffmanager-class.md)对象。

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>参数

*lpszRegEntry*<br/>
[在]包含注册表项路径的字符串。 应用程序在此注册表条目中存储撕下条的设置。

*乌伊蒂尔·乌梅首先*<br/>
[在]撕掉菜单的第一个菜单 ID。

*uiTearOffMenu 最后*<br/>
[在]撕掉菜单的最后一个菜单 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

菜单 ID 的范围从*uiTearOffMenuFirst*到*uiTearOffMenuLast，* 必须是连续间隔。 该间隔定义可在应用程序中同时显示的撕扯菜单数。

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenutearoff 管理器：：动态 ID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>参数

[在]*uiID*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearoff 经理：:P

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>参数

[在]*斯特*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearoff 管理器：重置

```cpp
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>参数

[在]*赫梅努*<br/>

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenutearoff 管理器：：Setinuse

```cpp
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>参数

[在]*乌伊CmDId*<br/>

[在]*bUse*<br/>

### <a name="remarks"></a>备注

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearoff 管理器：：设置"关闭菜单"

```cpp
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>参数

[在]*hMenu*<br/>

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
