---
title: "CBitmapButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs:
- C++
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d926e538cf9f9f1cb4935a1d53ba6c1fd7f4696e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cbitmapbutton-class"></a>CBitmapButton 类
创建使用位图图像而非文本进行标记的按钮控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CBitmapButton : public CButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|构造 `CBitmapButton` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|将在对话框中的按钮相关联的对象`CBitmapButton`类，按名称加载 bitmap(s) 和大小以适应位图按钮。|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|通过从应用程序的资源文件加载一个或多个命名的位图资源并将位图附加到对象初始化的对象。|  
|[CBitmapButton::SizeToContent](#sizetocontent)|调整大小以适应位图按钮。|  
  
## <a name="remarks"></a>备注  
 `CBitmapButton`对象包含最多四个位图，其中包含一个按钮可以假定不同状态的图像： 向上 （或正常），向下 （或所选），已设定焦点，且禁用。 只有第一个位图是必需的;其他是可选的。  
  
 位图按钮映像包括图像，以及图像本身的边框。 边框通常所起的作用中显示的按钮的状态。 例如，已设定焦点状态的位图通常就像一个对于松开状态但从边框或边界粗实线虚线的矩形内嵌。 位图的已禁用状态通常类似于一个松开状态但具有较低对比度 （如为灰色或显示为灰色菜单选择）。  
  
 这些位图可以是任意大小，但所有看做就好像它们是相同的大小最状态的位图。  
  
 各种应用程序要求位图图像的不同的组合：  
  
|向上|向下|已设定焦点|已禁用|应用程序|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Bitmap|  
|×|×|||按钮而无需**WS_TABSTOP**样式|  
|×|×|×|×|与所有状态对话框按钮|  
|×|×|×||使用对话框按钮**WS_TABSTOP**样式|  
  
 创建位图按钮控件时，设置**BS_OWNERDRAW**样式，可以指定按钮为所有者描述。 这会导致 Windows 发送`WM_MEASUREITEM`和`WM_DRAWITEM`按钮; 消息的框架处理这些消息，并管理为你的按钮的外观。  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在窗口的工作区中创建的位图按钮控件  
  
1.  创建一至四个位图图像的按钮。  
  
2.  构造[CBitmapButton](#cbitmapbutton)对象。  
  
3.  调用[创建](../../mfc/reference/cbutton-class.md#create)函数来创建 Windows 按钮控件并将其附加到`CBitmapButton`对象。  
  
4.  调用[LoadBitmaps](#loadbitmaps)成员函数以加载位图资源构造位图按钮之后。  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>若要包括在对话框中的位图按钮控件  
  
1.  创建一至四个位图图像的按钮。  
  
2.  使用放置到所需位图按钮其中一个所有者描述按钮创建对话框模板。 在模板的按钮的大小并不重要。  
  
3.  如按钮的标题设置为值" **MYIMAGE**"和定义按钮符号，如**IDC_MYIMAGE**。  
  
4.  在应用程序的资源脚本中，授予每个按钮创建通过附加一个字母"U，""D"、"F，"构造的 ID 的映像或者"X"（对应于向上、 向下侧重，并禁用） 按钮标题中使用的字符串到步骤 3。 按钮标题" **MYIMAGE**，"例如，将为 Id" **MYIMAGEU**，"" **MYIMAGED**，"" **MYIMAGEF**，"和" **MYIMAGEX**。" 你**必须**指定你在双引号内的位图的 ID。 否则为资源编辑器将分配给资源的一个整数，并且加载图像时，MFC 将失败。  
  
5.  在应用程序的对话框类 (派生自`CDialog`)，添加`CBitmapButton`成员对象。  
  
6.  在`CDialog`对象的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)例程，调用`CBitmapButton`对象的[自动上载](#autoload)函数，请使用作为参数按钮的控件 ID 和`CDialog`对象**这**指针。  
  
 如果你想要处理 Windows 通知消息，如**BN_CLICKED**、 发送到其父位图按钮控件 (通常从派生的类**CDialog)**，将添加到`CDialog`-派生对象为每个消息的消息映射条目和消息处理程序成员函数。 发送的通知`CBitmapButton`对象是由发送相同[CButton](../../mfc/reference/cbutton-class.md)对象。  
  
 类[CToolBar](../../mfc/reference/ctoolbar-class.md)针对位图按钮采用不同的方法。  
  
 有关详细信息`CBitmapButton`，请参阅[控件](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton::AutoLoad  
 将在对话框中的按钮相关联的对象`CBitmapButton`类，按名称加载 bitmap(s) 和大小以适应位图按钮。  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 按钮的控件 id。  
  
 `pParent`  
 指向拥有按钮的对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`AutoLoad`函数可以初始化为位图按钮的对话框中的所有者描述按钮。 有关使用此函数的说明是中的备注`CBitmapButton`类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 创建一个 `CBitmapButton` 对象。  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>备注  
 创建 c + + 之后`CBitmapButton`对象，请调用[CButton::Create](../../mfc/reference/cbutton-class.md#create)创建 Windows 按钮控件并将其附加到`CBitmapButton`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps  
 使用此函数，如果你想要加载标识由其资源名称或 ID 编号，或者无法使用的位图图像`AutoLoad`正常，因为，例如，要创建不属于对话框中的位图按钮。  
  
```  
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,  
    LPCTSTR lpszBitmapResourceSel = NULL,  
    LPCTSTR lpszBitmapResourceFocus = NULL,  
    LPCTSTR lpszBitmapResourceDisabled = NULL);

 
BOOL LoadBitmaps(
    UINT nIDBitmapResource,  
    UINT nIDBitmapResourceSel = 0,  
    UINT nIDBitmapResourceFocus = 0,  
    UINT nIDBitmapResourceDisabled = 0);
```  
  
### <a name="parameters"></a>参数  
 *lpszBitmapResource*  
 指向以 null 结尾的字符串包含位图的名称，如位图按钮的常规或"向上"状态。 必须的。  
  
 *lpszBitmapResourceSel*  
 点到包含位图的名称，为所选的位图按钮的以 null 结尾的字符串或"关闭"状态。 可能是**NULL**。  
  
 *lpszBitmapResourceFocus*  
 指向以 null 结尾的字符串，其中包含有关的位图按钮的已设定焦点状态的位图的名称。 可能是**NULL**。  
  
 *lpszBitmapResourceDisabled*  
 指向以 null 结尾的字符串包含位图按钮的禁用状态的位图的名称。 可能是**NULL**。  
  
 *nIDBitmapResource*  
 指定位图资源如位图按钮的常规或"向上"状态的资源 ID 号。 必须的。  
  
 *nIDBitmapResourceSel*  
 为所选的位图按钮的或"关闭"状态，请指定位图资源的资源 ID 号。 可能为 0。  
  
 *nIDBitmapResourceFocus*  
 指定位图按钮的已设定焦点状态的位图资源的资源 ID 号。 可能为 0。  
  
 *nIDBitmapResourceDisabled*  
 指定位图按钮的禁用状态的位图资源的资源 ID 号。 可能为 0。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 调用此函数可调整大小的位图的大小的位图按钮。  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CTRLTEST](../../visual-cpp-samples.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

