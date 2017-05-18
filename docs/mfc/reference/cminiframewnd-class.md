---
title: "CMiniFrameWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd class
- mini-frame windows
- toolbars [C++]
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7a7119a7317e8837c7ce672b2607a4e37b5239f5
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd 类
表示通常在浮动工具条周围出现的半高框架窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|构造 `CMiniFrameWnd` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|创建`CMiniFrameWnd`构造之后的对象。|  
|[CMiniFrameWnd::CreateEx](#createex)|创建`CMiniFrameWnd`（使用其他选项） 后构造的对象。|  
  
## <a name="remarks"></a>备注  
 这些微型框架窗口行为类似于普通的框架窗口，只不过它们不具有最大程度减少/最大化按钮或菜单和你只需单击系统菜单上，若要关闭它们。  
  
 若要使用`CMiniFrameWnd`对象，请首先定义对象。 然后调用[创建](#create)成员函数来显示微型框架窗口。  
  
 有关详细信息如何使用`CMiniFrameWnd`对象，请参阅文章[停靠和浮动工具栏](../../mfc/docking-and-floating-toolbars.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd  
 构造`CMiniFrameWnd`对象，但不会创建窗口。  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 若要创建的窗口，调用[CMiniFrameWnd::Create](#create)。  
  
##  <a name="create"></a>CMiniFrameWnd::Create  
 创建 Windows 微型框架窗口，并将其附加到`CMiniFrameWnd`对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpClassName`  
 指向以 null 结尾的字符串名称的 Windows 类。 类名称可以是具有全局注册的任何名称[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数。 如果**NULL**，将由框架为你注册窗口类。 MFC 提供了默认的类的以下样式和特性︰  
  
-   设置样式位**CS_DBLCLKS**，它会将双击消息到窗口过程当用户双击鼠标。  
  
-   设置样式位**CS_HREDRAW**和**CS_VREDRAW**，这指示客户端区域窗口更改大小时需要重新提取的内容。  
  
-   将类光标设置为 Windows 标准**IDC_ARROW**。  
  
-   将类背景画笔设置为**NULL**，因此窗口不会擦除其背景。  
  
-   将类图标设置为标准的、 飘扬标志 Windows 徽标图标。  
  
-   将窗口设置到的默认大小和位置，Windows 所述。  
  
 `lpWindowName`  
 指向以 null 结尾的字符串，其中包含窗口名称。  
  
 `dwStyle`  
 指定的窗口样式特性。 这些错误可能包括标准窗口样式和一个或多个以下的特殊样式︰  
  
- **MFS_MOVEFRAME**允许通过在窗口中，而不仅仅是标题任何边缘上单击要移动微型框架窗口。  
  
- **MFS_4THICKFRAME**禁用调整微型框架窗口的大小。  
  
- **MFS_SYNCACTIVE**同步微型框架窗口到其父窗口的激活的激活。  
  
- **MFS_THICKFRAME**允许微型框架窗口，因为客户端区域中的内容允许的最小大小。  
  
- **MFS_BLOCKSYSMENU**后将无法访问系统菜单和控制菜单中，并将它们转换为标题 （标题栏） 的一部分。  
  
 请参阅[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)有关可能的窗口样式值的说明。 典型的组合用于微型框架窗口是**WS_POPUP |WS_CAPTION |WS_SYSMENU**。  
  
 `rect`  
 A`RECT`结构，它指定所需的窗口的尺寸。  
  
 `pParentWnd`  
 向父窗口的点。 使用**NULL**为顶级窗口。  
  
 `nID`  
 如果用作子窗口创建微型框架窗口，则这是子控件; 标识符否则为 0。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 **创建**初始化窗口的类名称和窗口名称并注册其样式和父级的默认值。  
  
##  <a name="createex"></a>CMiniFrameWnd::CreateEx  
 创建一个 `CMiniFrameWnd` 对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定的扩展的样式`CMiniFrameWnd`正在创建。 应用任何[扩展窗口样式](../../mfc/reference/extended-window-styles.md)到窗口。  
  
 `lpClassName`  
 指向以 null 结尾的字符字符串名称的 Windows 类 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)结构)。 类名称可以是具有全局注册的任何名称[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)函数或任何预定义的控件类名称。 它不能**NULL**。  
  
 `lpWindowName`  
 指向以 null 结尾的字符串，其中包含窗口名称。  
  
 `dwStyle`  
 指定的窗口样式特性。 请参阅[窗口样式](../../mfc/reference/window-styles.md)和[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)有关可能的值的说明。  
  
 `rect`  
 大小和位置的窗口中，在客户端坐标中的`pParentWnd`。  
  
 `pParentWnd`  
 指向以父窗口对象。  
  
 `nID`  
 子窗口的标识符。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 `CreateEx`参数指定**WNDCLASS**，窗口样式和 （可选） 初始位置和窗口的大小。 `CreateEx`此外指定窗口的父级 （如果有） 和 id。  
  
 当`CreateEx`执行 Windows 发送[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)， [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)到窗口的消息。  
  
 若要扩展的默认消息处理，从派生类`CMiniFrameWnd`，将消息映射添加到新的类中，并为上述消息提供成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 重写进一步**上***消息*消息处理程序，以向派生类添加更多的功能。  
  
 如果**WS_VISIBLE**给定样式时，Windows 发送窗口激活和显示窗口所需的所有消息。 如果窗口样式指定的标题栏，窗口标题的指向`lpszWindowName`参数显示在标题栏中。  
  
 `dwStyle`参数可以是任意组合的[窗口样式](../../mfc/reference/window-styles.md)。  
  
 不再支持旧样式调色板工具箱窗口。 在以前版本的 Windows，运行 MFC 应用程序时，已支持的旧样式，没有"X"关闭按钮，但在 Visual c + +.NET 不再受支持。 仅新`WS_EX_TOOLWINDOW`样式现在支持; 这种样式的说明，请参阅[扩展窗口样式](../../mfc/reference/extended-window-styles.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)

