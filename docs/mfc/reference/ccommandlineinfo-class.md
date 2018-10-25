---
title: CCommandLineInfo 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5fd5eb6e4b58cbca21220bf6a7161505505dd3a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080541"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 类

辅助在应用程序启动时分析命令行。

## <a name="syntax"></a>语法

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|构造默认`CCommandLineInfo`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|重写此回调以分析每个参数。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|指示命令行`/Automation`找到选项。|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|指示命令行`/Embedding`找到选项。|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|指示是否应显示初始屏幕。|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|指示要处理的 shell 命令。|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|指示该驱动程序命名为外壳命令是打印到; 如果否则为空。|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|指示要打开或无法打印; 的文件名称如果 shell 命令新建或 DDE 为空。|
|[CCommandLineInfo::m_strPortName](#m_strportname)|指示该端口的 shell 命令是打印到; 如果名称否则为空。|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|指示打印机外壳命令是打印到; 如果名称否则为空。|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|如果重新启动管理器重新启动该应用程序重新启动管理器指示重启唯一标识符。|

## <a name="remarks"></a>备注

MFC 应用程序通常将创建此类中的本地实例[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)其应用程序对象的函数。 然后将此对象传递给[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)，从而会反复调用[ParseParam](#parseparam)填充`CCommandLineInfo`对象。 `CCommandLineInfo`对象然后传递给[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)处理命令行参数和标志。

可以使用此对象封装的以下命令行选项和参数：

|命令行参数|执行命令|
|----------------------------|----------------------|
|*app*|新的文件。|
|*应用*文件名|打开文件。|
|*应用程序*`/p`文件名|打印到默认打印机的文件。|
|*应用程序*`/pt`文件名打印机驱动程序端口|到指定的打印机的打印文件。|
|*应用程序* `/dde`|启动和 await DDE 命令。|
|*应用程序* `/Automation`|OLE 自动化服务器启动。|
|*应用程序* `/Embedding`|启动编辑嵌入的 OLE 项。|
|*应用程序* `/Register`<br /><br /> *应用程序* `/Regserver`|通知应用程序执行注册的任何任务。|
|*应用程序* `/Unregister`<br /><br /> *应用程序* `/Unregserver`|通知应用程序执行任何取消注册的任务。|

类派生新类从`CCommandLineInfo`以处理其他标志和参数值。 重写[ParseParam](#parseparam)来处理新的标志。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

此构造函数创建`CCommandLineInfo`具有默认值对象。

```
CCommandLineInfo();
```

### <a name="remarks"></a>备注

默认值是显示初始屏幕 ( `m_bShowSplash=TRUE`) 和文件菜单上执行新的命令 ( `m_nShellCommand` **= NewFile**)。

应用程序框架将调用[ParseParam](#parseparam)来填充此对象的数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

指示`/Automation`标志在命令行上找到。

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>备注

如果为 TRUE，这意味着为 OLE 自动化服务器启动。

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

指示`/Embedding`标志在命令行上找到。

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>备注

如果为 TRUE，这意味着启动以进行编辑嵌入的 OLE 项。

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

指示应显示初始屏幕。

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>备注

如果为 TRUE，这意味着此应用程序的初始屏幕应显示在启动过程。 默认实现[ParseParam](#parseparam)将此数据成员设置为 true [m_nShellCommand](#m_nshellcommand)等于`CCommandLineInfo::FileNew`。

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

指示此实例的应用程序的 shell 命令。

```
m_nShellCommand;
```

### <a name="remarks"></a>备注

此数据成员的类型是以下中定义的枚举的类型`CCommandLineInfo`类。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

有关这些值的简要说明，请参阅下面的列表。

- `CCommandLineInfo::FileNew` 指示命令行上，找到任何文件名称。

- `CCommandLineInfo::FileOpen` 指示，在命令行上找到文件名称和以下标志的任何命令行上未找到： `/p`， `/pt`， `/dde`。

- `CCommandLineInfo::FilePrint` 指示`/p`标志在命令行上找到。

- `CCommandLineInfo::FilePrintTo` 指示`/pt`标志在命令行上找到。

- `CCommandLineInfo::FileDDE` 指示`/dde`标志在命令行上找到。

- `CCommandLineInfo::AppRegister` 指示`/Register`或`/Regserver`标志找到命令行上，并要求应用程序以注册。

- `CCommandLineInfo::AppUnregister` 指示`/Unregister`或`/Unregserver`让应用程序已注销。

- `CCommandLineInfo::RestartByRestartManager` 指示重新启动管理器已重新启动该应用程序。

- `CCommandLineInfo::FileNothing` 关闭在启动新的 MDI 子窗口的显示。 根据设计，应用程序向导生成的 MDI 应用程序在启动时显示新的子窗口。 若要关闭此功能，应用程序可以使用`CCommandLineInfo::FileNothing`shell 命令调用时作为[processshellcommand 之后发生](../../mfc/reference/cwinapp-class.md#processshellcommand)。 `ProcessShellCommand` 调用`InitInstance( )`所有的`CWinApp`派生的类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

在命令行上存储的第三个非标志参数的值。

```
CString m_strDriverName;
```

### <a name="remarks"></a>备注

此参数通常是打印到 shell 命令的打印机驱动程序的名称。 默认实现[ParseParam](#parseparam)设置此数据成员仅当`/pt`标志在命令行上找到。

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

在命令行上存储的第一个非标志参数的值。

```
CString m_strFileName;
```

### <a name="remarks"></a>备注

此参数通常是文件的要打开的名称。

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

在命令行上存储的第四个非标志参数的值。

```
CString m_strPortName;
```

### <a name="remarks"></a>备注

此参数通常是打印到 shell 命令的打印机端口的名称。 默认实现[ParseParam](#parseparam)设置此数据成员仅当`/pt`标志在命令行上找到。

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

在命令行上存储的第二个非标志参数的值。

```
CString m_strPrinterName;
```

### <a name="remarks"></a>备注

此参数通常是打印机的打印到 shell 命令的名称。 默认实现[ParseParam](#parseparam)设置此数据成员仅当`/pt`标志在命令行上找到。

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

唯一的重新启动命令行上的标识符。

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>备注

重启标识符是唯一的应用程序的每个实例。

如果重新启动管理器退出应用程序，并且配置为重新启动它，重新启动管理器应用程序从命令行中使用的重启标识符作为执行一个可选参数。 当重新启动管理器使用的重启标识符时，该应用程序可以重新打开以前打开的文档，并恢复自动保存文件。

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

框架调用此函数可分析/解释每个参数从命令行。 第二个版本与前者区别仅在 Unicode 项目中。

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>参数

*pszParam*<br/>
参数或标志。

*bFlag*<br/>
指示是否*pszParam*是参数还是一个标志。

*冲击*<br/>
指示这是最后一个参数或在命令行上的标志。

### <a name="remarks"></a>备注

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)调用`ParseParam`一次为每个参数或在命令行上的标志，传递的参数*pszParam*。 如果该参数的第一个字符是 **-** 或**/**，则会将删除并*bFlag*设置为 TRUE。 分析最后一个参数时*冲击*设置为 TRUE。

此函数的默认实现可以识别以下标志： `/p`， `/pt`， `/dde`， `/Automation`，和`/Embedding`下, 表中所示：

|命令行参数|执行命令|
|----------------------------|----------------------|
|*app*|新的文件。|
|*应用*文件名|打开文件。|
|*应用程序*`/p`文件名|打印到默认打印机的文件。|
|*应用程序*`/pt`文件名打印机驱动程序端口|到指定的打印机的打印文件。|
|*应用程序* `/dde`|启动和 await DDE 命令。|
|*应用程序* `/Automation`|OLE 自动化服务器启动。|
|*应用程序* `/Embedding`|启动编辑嵌入的 OLE 项。|
|*应用程序* `/Register`<br /><br /> *应用程序* `/Regserver`|通知应用程序执行注册的任何任务。|
|*应用程序* `/Unregister`<br /><br /> *应用程序* `/Unregserver`|通知应用程序执行任何取消注册的任务。|

此信息存储在[m_bRunAutomated](#m_brunautomated)， [m_bRunEmbedded](#m_brunembedded)，并[m_nShellCommand](#m_nshellcommand)。 标志标记由正斜杠 '  **/** 或连字符**-**。

默认实现将放到第一个非标志参数[m_strFileName](#m_strfilename)。 情况下`/pt`标志的默认实现将第二个，放到第三个和第四个非标志参数[m_strPrinterName](#m_strprintername)， [m_strDriverName](#m_strdrivername)，并[m_strPortName](#m_strportname)分别。

默认实现还设置[m_bShowSplash](#m_bshowsplash)到仅在新的文件的情况下，则返回 TRUE。 如果是新文件，用户已执行涉及应用程序本身的操作。 在任何其他情况下，包括打开现有文件使用命令行程序，用户执行任何操作直接涉及该文件。 以文档为中心的角度来看，在不需要宣布启动该应用程序初始屏幕。

重写此函数在派生类来处理其他标志和参数值中。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

