---
title: "CAnimateCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [C++], CAnimateCtrl class
- Windows common controls [C++], CAnimateCtrl class
- CAnimateCtrl class
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
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
ms.openlocfilehash: cef1d6274d5334804ee028fa296c77faf124a496
ms.lasthandoff: 02/24/2017

---
# <a name="canimatectrl-class"></a>CAnimateCtrl 类
提供 Windows 公共动画控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|构造 `CAnimateCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|关闭 AVI 剪辑。|  
|[CAnimateCtrl::Create](#create)|创建动画控件，并将其附加到`CAnimateCtrl`对象。|  
|[CAnimateCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的动画控件并将其附加到`CAnimateCtrl`对象。|  
|[CAnimateCtrl::IsPlaying](#isplaying)|指示是否将正在播放的音频和视频交错 (AVI) 剪辑。|  
|[CAnimateCtrl::Open](#open)|从文件或资源打开 AVI 剪辑，显示的第一帧。|  
|[CAnimateCtrl::Play](#play)|播放 AVI 剪辑没有声音。|  
|[CAnimateCtrl::Seek](#seek)|显示所选的 AVI 剪辑单个帧。|  
|[CAnimateCtrl::Stop](#stop)|停止播放 AVI 剪辑。|  
  
## <a name="remarks"></a>备注  
 此控件 (并因此`CAnimateCtrl`类) 仅适用于在 Windows 95、 Windows 98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 动画控件是 AVI （音频和视频交错） 格式显示一个剪辑的矩形窗口 — 标准 Windows 视频/音频格式。 AVI 剪辑是一系列位图帧，与电影相似。  
  
 动画控件可以播放只是简单的 AVI 剪辑。 具体而言，动画控件要播放的剪辑必须满足以下要求︰  
  
-   必须恰好一个视频流，并且它必须具有至少一个框架。  
  
-   可以有最多两个流文件中 （通常在其他流 （如果存在） 是音频流，但在动画控件将忽略音频信息）。  
  
-   剪辑必须未压缩或 / / 使用 RLE8 压缩压缩。  
  
-   不调色板允许更改视频流中。  
  
 可以将 AVI 剪辑添加到您的应用程序作为 AVI 资源，或者它可以伴随您的应用程序作为单独的 AVI 文件。  
  
 由于您的线程会继续执行显示 AVI 剪辑时，动画控件的一个常见用途是在较长的操作期间指示系统活动。 例如，文件资源管理器查找对话框中将显示为系统搜索文件的移动的放大镜。  
  
 如果您创建`CAnimateCtrl`对象，在一个对话框，框中或通过使用对话框编辑器对话框资源，它将被自动销毁当用户关闭对话框。  
  
 如果您创建`CAnimateCtrl`对象在窗口中，您可能需要将其销毁。 如果您创建`CAnimateCtrl`对象在堆栈上，自动被销毁。 如果您创建`CAnimateCtrl`使用堆上的对象**新**函数，则必须调用**删除**对象以将其销毁。 如果派生新类从`CAnimateCtrl`和分配在该类中的任何内存，请重写`CAnimateCtrl`析构函数释放的分配。  
  
 有关详细信息使用`CAnimateCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-namecanimatectrla--canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl  
 构造 `CAnimateCtrl` 对象。  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>备注  
 必须调用[创建](#create)成员函数之前您还可以在您创建的对象上的任何其他操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&56;](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="a-nameclosea--canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Close  
 关闭以前打开过动画控件 （如果有） 中的 AVI 剪辑，并将其从内存中删除。  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="a-namecreatea--canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Create  
 创建动画控件，并将其附加到`CAnimateCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定动画控件的样式。 应用的 windows 下面的备注部分和动画控件样式中所述的样式中所述的任意组合[动画控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761886)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定动画控件的位置和大小。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](../../mfc/reference/rect-structure1.md)结构。  
  
 `pParentWnd`  
 指定动画控件的父窗口，通常`CDialog`。 它不能**NULL。**  
  
 `nID`  
 指定在动画控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 您构造`CAnimateCtrl`分两个步骤。 首先，调用构造函数中，，然后调用**创建**，它创建动画控件并将其附加到`CAnimateCtrl`对象。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到动画控件。  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 如果您想要扩展的窗口样式使用动画控件，调用[CreateEx](#createex)而不是**创建**。  
  
 除了上面列出的窗口样式，您可能想要将一个或多个动画控件样式应用于动画控件。 请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息[动画控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761886)。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="a-namecreateexa--canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CAnimateCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定动画控件的样式。 应用窗口的任意组合和动画控件样式中所述[动画控件样式](http://msdn.microsoft.com/library/windows/desktop/bb761886)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="a-nameisplayinga--canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::IsPlaying  
 指示是否将正在播放的音频和视频交错 (AVI) 剪辑。  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true`如果正在播放 AVI 剪辑;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameopena--canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Open  
 调用此函数可打开 AVI 剪辑，并显示其第一帧。  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 一个`CString`对象或指针以 null 结尾的字符串，其中包含的 AVI 文件的名称或 AVI 资源的名称。 如果此参数为**NULL**，由系统关闭以前已经打开了动画控件的 AVI 剪辑，如果有的话。  
  
 `nID`  
 AVI 资源标识符。 如果此参数为**NULL**，由系统关闭以前已经打开了动画控件的 AVI 剪辑，如果有的话。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 可从创建在动画控件的模块加载 AVI 资源。  
  
 **打开**AVI 剪辑; 中不支持声音可以打开静默 AVI 剪辑。  
  
 如果在动画控件具有`ACS_AUTOPLAY`样式，在动画控件将自动开始播放剪辑后将其打开。 它将继续在后台播放剪辑时线程会继续执行。 完成该剪辑播放时，它将自动重复。  
  
 如果在动画控件具有`ACS_CENTER`样式，将在控件中居中显示 AVI 剪辑和控件的大小将不会更改。 如果在动画控件不具有`ACS_CENTER`样式，将调整控件的大小，为 AVI 剪辑中的图像的大小打开 AVI 剪辑时。 该控件的左上角的位置不会改变，仅该控件的大小。  
  
 如果在动画控件具有`ACS_TRANSPARENT`样式，将使用具有透明背景色绘制第一帧而不是在中指定的背景色的动画剪辑。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="a-nameplaya--canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::Play  
 调用此函数可在动画控件中播放 AVI 剪辑。  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>参数  
 `nFrom`  
 开始播放帧的从零开始索引。 值必须是小于 65536。 值为 0 意味着开头 AVI 剪辑中的第一帧。  
  
 `nTo`  
 帧的从零开始的索引位置播放结束。 值必须是小于 65536。 该值为 – 1 表示结尾 AVI 剪辑中的最后一帧。  
  
 *nRep*  
 若要重播 AVI 剪辑的次数。 该值为 – 1 表示无限期地重播文件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 虽然线程会继续执行，动画控件将在后台播放剪辑。 如果在动画控件具有`ACS_TRANSPARENT`样式、 AVI 剪辑，将会播放使用背景色为透明，而不是指定动画剪辑中的背景色。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="a-nameseeka--canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Seek  
 调用此函数可静态显示 AVI 剪辑的单个帧。  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>参数  
 `nTo`  
 要显示的框架的从零开始索引。 值必须是小于 65536。 值为 0 意味着在 AVI 剪辑中显示的第一帧。 值 –&1; 表示在 AVI 剪辑中显示的最后一帧。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 如果在动画控件具有`ACS_TRANSPARENT`样式，将使用具有透明背景色绘制 AVI 剪辑而不是在中指定的背景色的动画剪辑。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
##  <a name="a-namestopa--canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Stop  
 调用此函数可停止在动画控件播放 AVI 剪辑。  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
  请参阅示例[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](http://msdn.microsoft.com/library/2cb7ebdf-296b-4606-b191-3449835003db)


