---
title: CKeyboardManager 类
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: e4f8f678e76113b5d012242f474ff0ab8b0628dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505784"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 类

管理主框架窗口和子框架窗口的快捷键表。

## <a name="syntax"></a>语法

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|构造 `CKeyboardManager` 对象。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CKeyboardManager::CleanUp](#cleanup)|清除快捷键表。|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|检索指定命令和窗口的默认快捷键。|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|确定键是否由快捷键对应表处理。|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|指示字符是否可打印。|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|指示菜单是显示命令的所有快捷键还是仅显示默认快捷键。|
|[CKeyboardManager::LoadState](#loadstate)|从 Windows 注册表加载快捷键表。|
|[CKeyboardManager::ResetAll](#resetall)|重新加载应用程序资源的快捷键表。|
|[CKeyboardManager::SaveState](#savestate)|将快捷键表保存到 Windows 注册表中。|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定框架是显示所有命令的所有快捷键, 还是为每个命令显示一个快捷键。 此方法不会影响只有一个关联快捷键的命令。|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|将字符转换为它的上限。|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|使用新的快捷键表更新快捷键表。|

## <a name="remarks"></a>备注

利用此类的成员, 您可以将快捷键表保存和加载到 Windows 注册表中, 使用模板更新简短的键表, 并在框架窗口中查找命令的默认快捷键。 此外, `CKeyboardManager`对象还允许您控制如何向用户显示快捷键。

不应手动创建`CKeyboardManager`对象。 应用程序的框架会自动创建它。 但是, 你应在应用程序的初始化过程中调用[CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) 。 若要获取应用程序的键盘管理器指针, 请调用[CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>示例

下面的示例演示如何`CKeyboardManager` `CWinAppEx`从类中检索指向对象的指针, 以及如何显示与菜单命令相关联的所有快捷键。 此代码片段是[自定义页面示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>要求

**标头:** afxkeyboardmanager

##  <a name="ckeyboardmanager"></a>CKeyboardManager:: CKeyboardManager

构造 `CKeyboardManager` 对象。

```
CKeyboardManager();
```

### <a name="remarks"></a>备注

在大多数情况下, 无需`CKeyboardManager`直接创建。 默认情况下, 框架为你创建一个。 若要获取指向的`CKeyboardManager`指针, 请调用[CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果手动创建一个, 则必须用方法[CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)对其进行初始化。

##  <a name="cleanup"></a>CKeyboardManager:: 清理

`CKeyboardManager`释放资源并清除所有快捷键映射。

```
static void CleanUp();
```

### <a name="remarks"></a>备注

有关快捷键的详细信息, 请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。

当应用程序退出时, 无需调用此函数, 因为框架会在应用程序退出期间自动调用它。

##  <a name="finddefaultaccelerator"></a>CKeyboardManager:: FindDefaultAccelerator

检索指定命令和窗口的默认快捷键。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中命令 ID。

*str*<br/>
弄对`CString`对象的引用。

*pWndFrame*<br/>
中指向框架窗口的指针。

*bIsDefaultFrame*<br/>
中指定框架窗口是否为默认框架窗口。

### <a name="return-value"></a>返回值

如果找到快捷方式, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此方法查找*uiCmd*指定的命令, 并检索默认快捷键。 然后, 该方法将使用与此快捷键相关联的字符串, 并将值写入*str*参数。

##  <a name="iskeyhandled"></a>CKeyboardManager:: IsKeyHandled

确定指定的键是否由[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)处理。

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*nKey*|中要检查的键。|
|*fVirt*|中指定快捷键的行为。 有关可能值的列表, 请参阅[加速结构](/windows/win32/api/winuser/ns-winuser-accel)。|
|*pWndFrame*|中框架窗口。 此方法确定快捷键是否在此帧中处理。|
|*bIsDefaultFrame*|中指示*pWndFrame*是否为默认框架窗口的布尔型参数。|

### <a name="return-value"></a>返回值

如果已处理快捷键, 则为 TRUE。 如果未处理该键, 则为 FALSE; 如果*pWndFrame*为 NULL, 则为 FALSE。

### <a name="remarks"></a>备注

输入参数必须与*nKey*和*fVirt*的快捷键对应表中的条目匹配, 以确定是否在*pWndFrame*中处理快捷键。

##  <a name="iskeyprintable"></a>CKeyboardManager:: IsKeyPrintable

指示字符是否可打印。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*nChar*|中此方法检查的字符。|

### <a name="return-value"></a>返回值

如果字符可打印, 则为非零; 否则为零。

### <a name="remarks"></a>备注

如果对[GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)的调用失败, 则此方法将失败。

##  <a name="isshowallaccelerators"></a>CKeyboardManager:: IsShowAllAccelerators

指示菜单是显示与菜单命令相关联的所有快捷键还是仅显示默认快捷键。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>返回值

如果应用程序列出了菜单命令的所有快捷键, 则为非零值;如果应用程序仅显示默认快捷键, 则为0。

### <a name="remarks"></a>备注

应用程序会在菜单栏中列出菜单命令的快捷键。 使用函数[CKeyboardManager:: ShowAllAccelerators](#showallaccelerators)可控制应用程序是列出所有快捷键还是只列出默认快捷键。

##  <a name="loadstate"></a>CKeyboardManager:: LoadState

从 Windows 注册表加载快捷键表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中保存`CKeyboardManager`数据的注册表路径。

*pDefaultFrame*<br/>
中指向要用作默认窗口的框架窗口的指针。

### <a name="return-value"></a>返回值

如果状态已成功加载, 则为非零; 否则为0。

### <a name="remarks"></a>备注

如果*lpszProfileName*参数为 NULL, 此方法将检查`CKeyboardManager`数据的默认注册表位置。 默认注册表位置由[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)指定。 数据以前必须用方法[CKeyboardManager:: SaveState](#savestate)来编写。

如果未指定默认窗口, 将使用应用程序的主框架窗口。

##  <a name="resetall"></a>CKeyboardManager:: ResetAll

重新加载应用程序资源的快捷键表。

```
void ResetAll();
```

### <a name="remarks"></a>备注

此函数清除`CKeyboardManager`实例中存储的快捷方式。 然后, 它将从应用程序资源重新加载键盘管理器的状态。

##  <a name="savestate"></a>CKeyboardManager:: SaveState

将快捷键表保存到 Windows 注册表中。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
中用于保存`CKeyboardManager`状态的注册表路径。

*pDefaultFrame*<br/>
中指向成为默认窗口的框架窗口的指针。

### <a name="return-value"></a>返回值

如果成功保存键盘管理器状态, 则为非零; 否则为0。

### <a name="remarks"></a>备注

如果*lpszProfileName*参数为 NULL, 则此方法会将`CKeyboardManager`状态写入[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)指定的默认位置。 如果指定位置, 则可以在以后使用方法[CKeyboardManager:: LoadState](#loadstate)加载数据。

如果未指定默认窗口, 将使用主框架窗口作为默认窗口。

##  <a name="showallaccelerators"></a>CKeyboardManager:: ShowAllAccelerators

显示与菜单命令相关联的所有快捷键。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>参数

*bShowAll*<br/>
中如果为 TRUE, 则将显示所有快捷键。 如果为 FALSE, 则只显示第一个快捷键。

*lpszDelimiter*<br/>
中要在快捷键之间插入的字符串。 如果只显示一个快捷键, 则此分隔符不起作用。

### <a name="remarks"></a>备注

默认情况下, 如果命令有多个关联的快捷键, 则只会显示第一个快捷键。 此函数使您能够列出与所有命令相关联的所有快捷键。

快捷键将在菜单栏中的命令旁边列出。 如果显示了所有快捷键, 则由*lpszDelimiter*提供的字符串将分隔单独的快捷键。

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

将字符转换为它的上限。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>参数

*nChar*<br/>
中要转换的字符。

### <a name="return-value"></a>返回值

作为输入参数的上限的字符。

##  <a name="updateacceltable"></a>CKeyboardManager:: UpdateAccelTable

使用新的快捷键表更新快捷键表。

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>参数

*pTemplate*<br/>
中指向文档模板的指针。

*lpAccel*<br/>
中指向新快捷键的指针。

*nSize*<br/>
中新快捷方式表的大小。

*pDefaultFrame*<br/>
中指向默认框架窗口的指针。

*hAccelNew*<br/>
中新快捷方式表的句柄。

### <a name="return-value"></a>返回值

如果方法成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

使用此函数可以将现有的快捷方式表替换为多个框架窗口对象的新快捷键。 函数接收文档模板作为参数, 以获取对连接到给定文档模板的所有框架窗口对象的访问权限。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)
