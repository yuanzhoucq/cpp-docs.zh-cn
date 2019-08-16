---
title: CUserTool 类
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502248"
---
# <a name="cusertool-class"></a>CUserTool 类

用户工具是运行外部应用程序的菜单项。 "**自定义**" 对话框 ( [CMFCToolBarsCustomizeDialog 类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) 的 "**工具**" 选项卡允许用户添加用户工具, 并为每个用户工具指定名称、命令、参数和初始目录。

## <a name="syntax"></a>语法

```
class CUserTool : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|在指定的矩形中绘制用户工具图标。|
|[CUserTool::GetCommand](#getcommand)|返回一个字符串, 该字符串包含与用户工具关联的命令的文本。|
|[CUserTool::GetCommandId](#getcommandid)|返回用户工具菜单项的命令 ID。|
|[CUserTool::Invoke](#invoke)|执行与用户工具关联的命令。|
|[CUserTool::Serialize](#serialize)|从存档读取该对象或将该对象写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[CUserTool::SetCommand](#setcommand)|设置与用户工具关联的命令。|
|[CUserTool::SetToolIcon](#settoolicon)|从与工具关联的应用程序中加载用户工具的图标。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|加载用户工具的默认图标。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|用户工具的命令行参数。|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|用户工具的初始目录。|
|[CUserTool::m_strLabel](#m_strlabel)|工具的菜单项中显示的工具名称。|

## <a name="remarks"></a>备注

有关如何在应用程序中启用用户工具的详细信息, 请参阅[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。

## <a name="example"></a>示例

下面的示例演示如何从`CUserToolsManager`对象创建工具、 `m_strLabel`设置成员变量以及设置用户工具运行的应用程序。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>要求

**标头:** afxusertool

##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="drawtoolicon"></a>CUserTool::D rawToolIcon

在指定矩形的中心绘制 "用户工具" 图标。

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rectImage*<br/>
中指定显示图标的区域的坐标。

##  <a name="getcommand"></a>CUserTool:: GetCommand

返回一个字符串, 该字符串包含与用户工具关联的命令的文本。

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>返回值

对`CString`对象的引用, 该对象包含与用户工具关联的命令的文本。

##  <a name="getcommandid"></a>CUserTool::GetCommandId

返回用户工具的命令 ID。

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>返回值

此用户工具的命令 ID。

##  <a name="invoke"></a>CUserTool:: Invoke

执行与用户工具关联的命令。

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>返回值

如果命令成功执行, 则为非零值;否则为0。

### <a name="remarks"></a>备注

调用[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)来执行与用户工具关联的命令。 如果命令为空或[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)失败, 则函数会失败。

##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

加载用户工具的默认图标。

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>返回值

加载的图标 (HICON) 的句柄; 如果无法加载默认图标, 则为 NULL。

### <a name="remarks"></a>备注

当框架无法从工具的可执行文件中加载用户定义的工具图标时, 框架会调用此方法。

重写此方法以提供您自己的默认工具图标。

##  <a name="m_strarguments"></a>CUserTool::m_strArguments

用户工具的命令行参数。

```
CString m_strArguments;
```

### <a name="remarks"></a>备注

当你调用[CUserTool:: Invoke](#invoke)时, 或当用户单击与此工具关联的命令时, 此字符串将传递给该工具。

##  <a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

为用户工具指定初始目录。

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>备注

此变量指定当你调用[CUserTool:: Invoke](#invoke)时或用户单击与此工具关联的命令时, 该工具在中执行的初始目录。

##  <a name="m_strlabel"></a>CUserTool::m_strLabel

显示在工具的菜单项中的标签。

```
CString m_strLabel;
```

##  <a name="serialize"></a>CUserTool:: 串行化

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

[in] *ar*<br/>

### <a name="remarks"></a>备注

##  <a name="setcommand"></a>CUserTool::SetCommand

设置用户工具运行的应用程序。

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>参数

*lpszCmd*<br/>
中指定要与用户工具关联的新应用程序。

### <a name="remarks"></a>备注

调用此方法可设置用户工具运行的新应用程序。 方法会销毁旧图标, 并从给定的应用程序中加载新图标。 如果无法从应用程序中加载图标, 它会通过调用[CUserTool:: LoadDefaultIcon](#loaddefaulticon)加载用户工具的默认图标。

##  <a name="settoolicon"></a>CUserTool::SetToolIcon

从工具使用的应用程序中加载用户工具的图标。

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>返回值

加载的图标的句柄。

### <a name="remarks"></a>备注

调用此方法以加载要在菜单项上显示的图标。 此方法在工具使用的可执行文件中搜索图标。 如果它没有默认图标, 则改为使用[CUserTool:: LoadDefaultIcon](#loaddefaulticon)提供的图标。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)
