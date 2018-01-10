---
title: "CHotKeyCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
dev_langs: C++
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 982d4dec9c00490248da0b0e0dec7fd44376c218
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl 类
提供 Windows 公共热键控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|构造 `CHotKeyCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHotKeyCtrl::Create](#create)|创建热键控件并将其附加到`CHotKeyCtrl`对象。|  
|[CHotKeyCtrl::CreateEx](#createex)|创建指定的 Windows 扩展样式热键控件，并将其附加到`CHotKeyCtrl`对象。|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|从热键控件中检索热键的虚拟键代码和修饰符标志。|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|检索分配给热键的本地字符集中的密钥名称。|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|检索分配给指定的虚拟键代码的本地字符集中的密钥名称。|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|设置热键控件热键组合。|  
|[CHotKeyCtrl::SetRules](#setrules)|定义的无效组合和热键控件的默认修饰符组合。|  
  
## <a name="remarks"></a>备注  
 "热键控件"是一个窗口，使用户能够创建热键。 "热键"是用户可以按操作更快地执行的键组合。 （例如，用户可以创建一个用于激活给定的窗口并将其置于 Z 顺序的顶层热键。）热键控件将显示用户的选择，并确保用户选择有效的键组合。  
  
 此控件 (因此`CHotKeyCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 应用程序时用户已选择键组合，可以从控件中检索指定的键组合并使用**WM_SETHOTKEY**设置热键在系统中的消息。 每当用户按热键此后，从系统的任何部分中指定窗口**WM_SETHOTKEY**消息接收`WM_SYSCOMMAND`消息指定**SC_HOTKEY**。 此消息激活接收的窗口。 热键的应用程序调用之前就保持有效**WM_SETHOTKEY**退出。  
  
 此机制是不同于依赖于的热密钥支持**WM_HOTKEY**消息和 Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)和[UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327)函数。  
  
 有关详细信息使用`CHotKeyCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl  
 构造 `CHotKeyCtrl` 对象。  
  
```  
CHotKeyCtrl();
```  
  
##  <a name="create"></a>CHotKeyCtrl::Create  
 创建热键控件并将其附加到`CHotKeyCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定热键控件的样式。 应用控件样式的任意组合。 请参阅[公共控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)适用于详细信息的 Windows SDK 中。  
  
 `rect`  
 指定热键控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](../../mfc/reference/rect-structure1.md)。  
  
 `pParentWnd`  
 通常指定热键控件的父窗口[CDialog](../../mfc/reference/cdialog-class.md)。 它不能**NULL**。  
  
 `nID`  
 指定热键控件的 id。  
  
### <a name="return-value"></a>返回值  
 不为零，如果初始化成功;否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CHotKeyCtrl`两个步骤中的对象。 首先，调用的构造函数，然后调用**创建**，它创建热键控件并将其附加到`CHotKeyCtrl`对象。  
  
 如果你想要将扩展的窗口样式与控件一起使用，调用[CreateEx](#createex)而不是**创建**。  
  
##  <a name="createex"></a>CHotKeyCtrl::CreateEx  
 调用此函数可创建的控件 （子窗口），并将其与关联`CHotKeyCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `dwStyle`  
 指定热键控件的样式。 应用控件样式的任意组合。 有关详细信息，请参阅[公共控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)Windows SDK 中。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="gethotkey"></a>CHotKeyCtrl::GetHotKey  
 从热键控件中检索的键盘快捷方式的虚拟键代码和修饰符标志。  
  
```  
DWORD GetHotKey() const;  
  
void GetHotKey(
    WORD& wVirtualKeyCode,  
    WORD& wModifiers) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `wVirtualKeyCode`  
 键盘快捷方式的虚拟键代码。 有关标准虚拟键代码的列表，请参见 Winuser.h。  
  
 [out] `wModifiers`  
 指示修改键的键盘快捷方式中的标志的按位组合 (OR)。  
  
 修饰符标志如下所示：  
  
|Flag|相应的密钥|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|Alt 键|  
|`HOTKEYF_CONTROL`|CTRL 键|  
|`HOTKEYF_EXT`|扩展的密钥|  
|`HOTKEYF_SHIFT`|Shift 键|  
  
### <a name="return-value"></a>返回值  
 在第一个重载的方法，`DWORD`包含虚拟键代码和修饰符标志。 低序位字的低序位字节包含的虚拟键代码、 低序位字的高序位字节包含修饰符标志和高序位字为零。  
  
### <a name="remarks"></a>备注  
 虚拟键代码和修改键组合在一起定义的键盘快捷方式。  
  
##  <a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName  
 调用此成员函数可获取热键的本地化的名称。  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前所选的热键本地化的名称。 如果没有任何所选的热键`GetHotKeyName`返回空字符串。  
  
### <a name="remarks"></a>备注  
 此成员函数返回的名称是从键盘驱动程序。 你可以安装的非本地化键盘驱动程序中的本地化版本的 Windows 中，反之亦然。  
  
##  <a name="getkeyname"></a>CHotKeyCtrl::GetKeyName  
 调用此成员函数可获取分配给指定的虚拟键代码的键的本地化的名称。  
  
```  
static CString GetKeyName(
    UINT vk,  
    BOOL fExtended);
```  
  
### <a name="parameters"></a>参数  
 `vk`  
 虚拟键代码。  
  
 *fExtended*  
 如果虚拟键代码是否为扩展的键， **TRUE**; 否则为**FALSE**。  
  
### <a name="return-value"></a>返回值  
 指定的键的本地化的名称`vk`参数。 如果密钥没有映射的名称，`GetKeyName`返回空字符串。  
  
### <a name="remarks"></a>备注  
 此函数将返回的项名称来自键盘驱动程序，因此你可以安装的非本地化键盘驱动程序中的本地化版本的 Windows 中，反之亦然。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]  
  
##  <a name="sethotkey"></a>CHotKeyCtrl::SetHotKey  
 设置热键控件的键盘快捷方式。  
  
```  
void SetHotKey(
    WORD wVirtualKeyCode,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>参数  
 [in] `wVirtualKeyCode`  
 键盘快捷方式的虚拟键代码。 有关标准虚拟键代码的列表，请参见 Winuser.h。  
  
 [in] `wModifiers`  
 指示修改键的键盘快捷方式中的标志的按位组合 (OR)。  
  
 修饰符标志如下所示：  
  
|Flag|相应的密钥|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|Alt 键|  
|`HOTKEYF_CONTROL`|CTRL 键|  
|`HOTKEYF_EXT`|扩展的密钥|  
|`HOTKEYF_SHIFT`|Shift 键|  
  
### <a name="remarks"></a>备注  
 虚拟键代码和修改键组合在一起定义的键盘快捷方式。  
  
##  <a name="setrules"></a>CHotKeyCtrl::SetRules  
 调用此函数可定义的无效组合和热键控件的默认修饰符组合。  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>参数  
 `wInvalidComb`  
 指定无效的键组合的数组的标志。 它可以是以下值的组合：  
  
- `HKCOMB_A`ALT  
  
- `HKCOMB_C`CTRL  
  
- `HKCOMB_CA`CTRL + ALT  
  
- `HKCOMB_NONE`未修改的键  
  
- `HKCOMB_S`SHIFT  
  
- `HKCOMB_SA`SHIFT + ALT  
  
- `HKCOMB_SC`SHIFT + CTRL  
  
- `HKCOMB_SCA`SHIFT + CTRL + ALT  
  
 `wModifiers`  
 指定键的组合用户输入的无效组合时要使用的数组的标志。 修饰符标志的详细信息，请参阅[GetHotKey](#gethotkey)。  
  
### <a name="remarks"></a>备注  
 当用户输入无效的键组合，由中指定的标志所规定`wInvalidComb`，系统使用 OR 运算符以组合中指定的标志与用户输入的密钥`wModifiers`。 生成的键组合将转换为字符串，然后显示在热键控件。  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



