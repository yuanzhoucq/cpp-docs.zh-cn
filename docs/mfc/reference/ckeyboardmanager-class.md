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
ms.openlocfilehash: a8053ab33a2b49eb2c447cdaa1cb2b9e356bc696
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754925"
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
|名称|说明|
|[键盘管理器：键盘管理器](#ckeyboardmanager)|构造 `CKeyboardManager` 对象。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[键盘管理器：：清理](#cleanup)|清除快捷键表。|
|[键盘管理器：：查找默认加速器](#finddefaultaccelerator)|检索指定命令和窗口的默认快捷键。|
|[键盘管理器：：按键处理](#iskeyhandled)|确定密钥是否由加速器表处理。|
|[键盘管理器：可键打印](#iskeyprintable)|指示字符是否可打印。|
|[键盘管理器：：是显示所有加速器](#isshowallaccelerators)|指示菜单是显示命令的所有快捷键还是仅显示默认快捷键。|
|[键盘管理器：：加载状态](#loadstate)|从 Windows 注册表加载快捷键表。|
|[键盘管理器：：重置所有](#resetall)|从应用程序资源重新加载快捷键表。|
|[键盘管理器：：保存状态](#savestate)|将快捷键表保存到 Windows 注册表。|
|[键盘管理器：：显示所有加速器](#showallaccelerators)|指定框架是显示所有命令的所有快捷键，还是显示每个命令的单个快捷键。 此方法不会影响只有一个关联的快捷键的命令。|
|[键盘管理器：：翻译字符上部](#translatechartoupper)|将字符转换为其上寄存器。|
|[键盘管理器：：更新AccelTable](#updateacceltable)|使用新的快捷键表更新快捷键表。|

## <a name="remarks"></a>备注

此类的成员使您能够将快捷键表保存到 Windows 注册表，使用模板更新短切键表，并在框架窗口中查找命令的默认快捷键。 此外，`CKeyboardManager`该对象允许您控制向用户显示快捷键的方式。

不应手动创建`CKeyboardManager`对象。 它将由应用程序的框架自动创建。 但是，您应该在应用程序的初始化过程中调用[CWinAppEx：init键盘管理器](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。 要获取指向应用程序的键盘管理器的指针，请致电[CWinAppEx：：get键盘管理器](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>示例

下面的示例演示如何从`CKeyboardManager``CWinAppEx`类检索指向对象的指针，以及如何显示与菜单命令关联的所有快捷键。 此代码段是[自定义页示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>要求

**标题：** afx键盘管理器.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>键盘管理器：键盘管理器

构造 `CKeyboardManager` 对象。

```
CKeyboardManager();
```

### <a name="remarks"></a>备注

在大多数情况下，您不必直接创建 。 `CKeyboardManager` 默认情况下，框架会为您创建一个。 要获取 指向 的`CKeyboardManager`指针，请致电[CWinAppEx：：获取键盘管理器](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果手动创建一个，则必须使用[方法 CWinAppEx：：init键盘管理器](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)初始化它。

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>键盘管理器：：清理

释放`CKeyboardManager`资源并清除所有快捷键映射。

```
static void CleanUp();
```

### <a name="remarks"></a>备注

有关快捷键的详细信息，请参阅[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)。

当应用程序退出时，您不必调用此功能，因为框架会在应用程序退出期间自动调用它。

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>键盘管理器：：查找默认加速器

检索指定命令和窗口的默认快捷键。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]命令 ID。

*Str*<br/>
[出]对对象的引用`CString`。

*pWndFrame*<br/>
[在]指向框架窗口的指针。

*bIsDefaultFrame*<br/>
[在]指定框架窗口是否为默认框架窗口。

### <a name="return-value"></a>返回值

如果找到快捷方式，则非零;否则 0。

### <a name="remarks"></a>备注

此方法查找*uiCmd*指定的命令并检索默认快捷键。 然后，该方法获取与此快捷键关联的字符串，并将值写入*str*参数。

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>键盘管理器：：按键处理

确定指定的密钥是否由[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)处理。

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
|参数|说明|
|*n键*|[在]要检查的键。|
|*fVirt*|[在]指定快捷键的行为。 有关可能值的列表，请参阅[ACCEL 结构](/windows/win32/api/winuser/ns-winuser-accel)。|
|*pWndFrame*|[在]框架窗口。 此方法确定是否在此帧中处理快捷键。|
|*bIsDefaultFrame*|[在]指示*pWndFrame*是否为默认帧窗口的布尔参数。|

### <a name="return-value"></a>返回值

如果处理快捷键，则为 TRUE。 如果未处理密钥或*pWndFrame*为 NULL，则 FALSE。

### <a name="remarks"></a>备注

输入参数必须匹配*nKey*和*fVirt*的加速器表中的条目，以确定是否在*pWndFrame*中处理快捷键。

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>键盘管理器：可键打印

指示字符是否可打印。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*n查尔*|[在]此方法检查的字符。|

### <a name="return-value"></a>返回值

如果字符可打印，则为非零，如果不是，则为零。

### <a name="remarks"></a>备注

如果对[GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)的调用失败，此方法将失败。

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>键盘管理器：：是显示所有加速器

指示菜单是显示与菜单命令关联的所有快捷键，还是仅显示默认快捷键。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>返回值

如果应用程序列出了菜单命令的所有快捷键，则非零;如果应用程序仅显示默认快捷键，则为 0。

### <a name="remarks"></a>备注

应用程序在菜单栏中列出菜单命令的快捷键。 使用函数[CKeyboardManager：：ShowAllAccelerators](#showallaccelerators)控制应用程序是否列出所有快捷键还是仅列出默认快捷键。

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>键盘管理器：：加载状态

从 Windows 注册表加载快捷键表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]保存`CKeyboardManager`数据的注册表路径。

*pDefaultFrame*<br/>
[在]指向帧窗口的指针，用于默认窗口。

### <a name="return-value"></a>返回值

如果状态已成功加载，则为非零，否则为 0。

### <a name="remarks"></a>备注

如果*lpszProfileName*参数为 NULL，则此方法将检查`CKeyboardManager`数据的默认注册表位置。 默认注册表位置由[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)指定。 数据以前必须使用方法[CKeyboardManager：：：：保存状态](#savestate)编写。

如果不指定默认窗口，将使用应用程序的主框架窗口。

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>键盘管理器：：重置所有

从应用程序资源重新加载快捷键表。

```cpp
void ResetAll();
```

### <a name="remarks"></a>备注

此函数清除存储在实例中的`CKeyboardManager`快捷方式。 然后，它将从应用程序资源重新加载键盘管理器的状态。

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>键盘管理器：：保存状态

将快捷键表保存到 Windows 注册表。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]用于保存状态的`CKeyboardManager`注册表路径。

*pDefaultFrame*<br/>
[在]指向帧窗口的指针，该指针将成为默认窗口。

### <a name="return-value"></a>返回值

如果键盘管理器状态已成功保存，则为非零，否则为 0。

### <a name="remarks"></a>备注

如果*lpszProfileName*参数为 NULL，则此方法将`CKeyboardManager`状态写入[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)指定的默认位置。 如果指定位置，则可以稍后使用方法[CKeyboardManager：：：LoadState](#loadstate)加载数据。

如果不指定默认窗口，则主框架窗口将用作默认窗口。

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>键盘管理器：：显示所有加速器

显示与菜单命令关联的所有快捷键。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>参数

*b显示全部*<br/>
[在]如果为 TRUE，将显示所有快捷键。 如果 FALSE，则仅显示第一个快捷键。

*lpsz 分隔符*<br/>
[在]要在快捷键之间插入的字符串。 如果只显示一个快捷键，则此分隔符不起作用。

### <a name="remarks"></a>备注

默认情况下，如果命令有多个与其关联的快捷键，则仅显示第一个快捷键。 此功能使您能够列出与所有命令关联的所有快捷键。

快捷键将列在菜单栏中命令旁边。 如果显示所有快捷键，*则 lpszDelimiter*提供的字符串将分隔各个快捷键。

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>键盘管理器：：翻译字符上部

将字符转换为其上寄存器。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>参数

*n查尔*<br/>
[在]要转换的字符。

### <a name="return-value"></a>返回值

作为输入参数的上部寄存器的字符。

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>键盘管理器：：更新AccelTable

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
[在]指向文档模板的指针。

*lpAccel*<br/>
[在]指向新快捷键的指针。

*nSize*<br/>
[在]新快捷方式表的大小。

*pDefaultFrame*<br/>
[在]指向默认帧窗口的指针。

*哈克尔新*<br/>
[在]新快捷方式表的句柄。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

使用此函数可以将现有快捷表替换为多个框架窗口对象的新快捷键。 该函数接收文档模板作为参数，以获取对连接到给定文档模板的所有帧窗口对象的访问。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx：：Init键盘管理器](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)
