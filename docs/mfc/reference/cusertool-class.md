---
title: 用户工具类
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
ms.openlocfilehash: 183b30961e4a7d3079fa0d035a4ddc38bc2eebac
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752029"
---
# <a name="cusertool-class"></a>用户工具类

用户工具是运行外部应用程序的菜单项。 **"自定义"** 对话框的 **"工具**"选项卡 （ [CMFCToolBars 自定义对话框类](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)） 使用户能够添加用户工具，并为每个用户工具指定名称、命令、参数和初始目录。

## <a name="syntax"></a>语法

```
class CUserTool : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[用户工具：：复制图标到剪贴板](#copyicontoclipboard)||
|[用户工具：:D原始工具图标](#drawtoolicon)|在指定的矩形中绘制用户工具图标。|
|[用户工具：：获取命令](#getcommand)|返回包含与用户工具关联的命令文本的字符串。|
|[用户工具：：获取命令 Id](#getcommandid)|返回用户工具的菜单项的命令 ID。|
|[用户工具：：调用](#invoke)|执行与用户工具关联的命令。|
|[用户工具：：序列化](#serialize)|从存档读取该对象或将该对象写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[用户工具：：设置命令](#setcommand)|设置与用户工具关联的命令。|
|[用户工具：：设置工具图标](#settoolicon)|从与该工具关联的应用程序加载用户工具的图标。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[用户工具：：加载默认图标](#loaddefaulticon)|加载用户工具的默认图标。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[用户工具：：m_strArguments](#m_strarguments)|用户工具的命令行参数。|
|[用户工具：：m_strInitialDirectory](#m_strinitialdirectory)|用户工具的初始目录。|
|[用户工具：：m_strLabel](#m_strlabel)|工具菜单项中显示的工具名称。|

## <a name="remarks"></a>备注

有关如何在应用程序中启用用户工具的详细信息，请参阅[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)。

## <a name="example"></a>示例

下面的示例演示如何从`CUserToolsManager`对象创建工具、设置`m_strLabel`成员变量以及设置用户工具运行的应用程序。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>要求

**标题：** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>用户工具：：复制图标到剪贴板

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>用户工具：:D原始工具图标

在指定矩形的中心绘制用户工具图标。

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectImage*<br/>
[在]指定要显示图标的区域的坐标。

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>用户工具：：获取命令

返回包含与用户工具关联的命令文本的字符串。

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>返回值

对`CString`包含与用户工具关联的命令文本的对象的引用。

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>用户工具：：获取命令 Id

返回用户工具的命令 ID。

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>返回值

此用户工具的命令 ID。

## <a name="cusertoolinvoke"></a><a name="invoke"></a>用户工具：：调用

执行与用户工具关联的命令。

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>返回值

如果命令成功执行，则非零;否则 0。

### <a name="remarks"></a>备注

调用[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)以执行与用户工具关联的命令。 如果命令为空或[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)失败，则函数将失败。

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>用户工具：：加载默认图标

加载用户工具的默认图标。

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>返回值

如果无法加载默认图标，则对加载的图标 （HICON） 或 NULL 的句柄。

### <a name="remarks"></a>备注

当框架无法从该工具的可执行文件加载用户定义工具的图标时，该框架将调用此方法。

重写此方法以提供您自己的默认工具图标。

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>用户工具：：m_strArguments

用户工具的命令行参数。

```
CString m_strArguments;
```

### <a name="remarks"></a>备注

当您调用[CUserTool：：：Invoke](#invoke)或当用户单击与此工具关联的命令时，此字符串将传递给该工具。

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>用户工具：：m_strInitialDirectory

指定用户工具的初始目录。

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>备注

此变量指定工具在调用[CUserTool：：Invoke](#invoke)或当用户单击与此工具关联的命令时执行的初始目录。

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>用户工具：：m_strLabel

工具的菜单项中显示的标签。

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>用户工具：：序列化

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

[在]*阿尔*<br/>

### <a name="remarks"></a>备注

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>用户工具：：设置命令

设置用户工具运行的应用程序。

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>参数

*lpszCmd*<br/>
[在]指定要与用户工具关联的新应用程序。

### <a name="remarks"></a>备注

调用此方法以设置用户工具运行的新应用程序。 该方法将销毁旧图标并加载给定应用程序的新图标。 如果无法从应用程序加载图标，则通过调用[CUserTool：：LoadDefaultIcon](#loaddefaulticon)来加载用户工具的默认图标。

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>用户工具：：设置工具图标

从该工具使用的应用程序加载用户工具的图标。

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>返回值

加载图标的句柄。

### <a name="remarks"></a>备注

调用此方法以加载要显示在菜单项上的图标。 此方法搜索该工具使用的可执行文件中的图标。 如果没有默认图标，则使用[CUserTool：：LoadDefaultIcon](#loaddefaulticon)提供的图标。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager 类](../../mfc/reference/cusertoolsmanager-class.md)
