---
title: "CBitmapButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- buttons, bitmap
- CBitmapButton class
- bitmaps, button controls
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 22
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
ms.sourcegitcommit: 0b07f6b12e178d8e324313ea3b0f6de9ae7420c9
ms.openlocfilehash: 16d39cb380b75e6dcef71dda01626f120d5c12fb
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|将在对话框中的按钮相关联的对象与`CBitmapButton`类中，按名称加载 bitmap(s) 和大小以适合该位图的按钮。|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|通过从应用程序的资源文件加载一个或多个命名的位图资源并将位图附加到对象来初始化对象。|  
|[CBitmapButton::SizeToContent](#sizetocontent)|调整大小以容纳该位图的按钮。|  
  
## <a name="remarks"></a>备注  
 `CBitmapButton`对象包含最多四个包含一个按钮可以承担的不同状态的图像的位图︰ 向上 （或普通），向下 （或所选），中心，且禁用。 只有第一个位图是必需的;有些则是可选的。  
  
 位图按钮的图像包括为图像本身或图像周围的边框。 边框通常在发挥作用显示按钮的状态。 例如，具有焦点的状态的位图通常是类似的松开状态但从边框或边界的粗实线虚线的矩形嵌入了。 位图为禁用状态通常类似于一个松开状态但具有较低的对比度 （像灰显或灰色菜单选择）。  
  
 这些位图可以是任意大小的但所有看做就好像它们是与松开状态的位图的大小相同。  
  
 各种应用程序需要不同的位图图像的组合︰  
  
|向上|向下|已设定焦点|已禁用|应用程序|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Bitmap|  
|×|×|||按钮而无需**WS_TABSTOP**样式|  
|×|×|×|×|与所有状态对话框按钮|  
|×|×|×||使用对话框按钮**WS_TABSTOP**样式|  
  
 创建位图按钮控件时，设置**BS_OWNERDRAW**指定按钮为所有者描述的样式。 这会导致 Windows 向发送`WM_MEASUREITEM`和`WM_DRAWITEM`的按钮，则消息框架如何处理这些消息，并管理您按钮的外观。  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在窗口的工作区中创建的位图按钮控件  
  
1.  创建一至四个位图图像的按钮。  
  
2.  构造[CBitmapButton](#cbitmapbutton)对象。  
  
3.  调用[创建](../../mfc/reference/cbutton-class.md#create)函数创建的 Windows 按钮控件并将其附加到`CBitmapButton`对象。  
  
4.  调用[LoadBitmaps](#loadbitmaps)成员函数以在构造位图按钮之后加载位图资源。  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>若要在对话框中包含的位图按钮控件  
  
1.  创建一至四个位图图像的按钮。  
  
2.  使用一个所有者绘制按钮放置需位图按钮的位置创建对话框模板。 在模板中按钮的大小并不重要。  
  
3.  设置按钮的标题为一个值，如" **MYIMAGE**"和定义按钮的符号，如**IDC_MYIMAGE**。  
  
4.  在应用程序的资源脚本中，为每个构造通过附加的一个字母"U，""D"、"F"、 ID 为按钮创建的映像或者"X"（对于向上、 下、 已设定焦点，并禁用） 用于在按钮标题的字符串到步骤 3。 按钮标题为" **MYIMAGE**，"例如，Id 将" **MYIMAGEU**，"" **MYIMAGED**，"" **MYIMAGEF**，"和" **MYIMAGEX**。" 您**必须**指定在双引号内位图的 ID。 否则为资源编辑器将分配给资源的一个整数，并在加载图像时，MFC 将会失败。  
  
5.  在您的应用程序的对话框类 (派生自`CDialog`)，添加`CBitmapButton`成员对象。  
  
6.  在`CDialog`对象的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)例程，调用`CBitmapButton`对象的[AutoLoad](#autoload)函数，请使用作为参数的按钮控件 ID 和`CDialog`对象的**这**指针。  
  
 如果想要处理 Windows 通知消息，如**BN_CLICKED**、 已发送到其父级的位图按钮控件 (通常派生自该类**CDialog)**，将添加到`CDialog`-派生对象消息映射条目和消息处理程序成员函数，为每个消息。 发送的通知`CBitmapButton`对象是否不同于由发送[CButton](../../mfc/reference/cbutton-class.md)对象。  
  
 此类[CToolBar](../../mfc/reference/ctoolbar-class.md)位图按钮到采用不同的方法。  
  
 有关详细信息`CBitmapButton`，请参阅[控件](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton::AutoLoad  
 将在对话框中的按钮相关联的对象与`CBitmapButton`类中，按名称加载 bitmap(s) 和大小以适合该位图的按钮。  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 该按钮的控件 id。  
  
 `pParent`  
 指向拥有按钮的对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`AutoLoad`函数以便初始化为位图按钮的对话框中的一个所有者绘制按钮。 中的备注的说明使用此函数`CBitmapButton`类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&75;](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 创建一个 `CBitmapButton` 对象。  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>备注  
 创建 c + + 后`CBitmapButton`对象，请调用[CButton::Create](../../mfc/reference/cbutton-class.md#create)创建 Windows 按钮控件并将其附加到`CBitmapButton`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&57;](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps  
 如果你想要加载位图图像按其资源名称或 ID 号或不能使用应用程序识别使用此函数`AutoLoad`正常，因为; 例如，将创建一个不属于对话框中的位图按钮。  
  
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
 指向以 null 结尾的字符串，其中包含为位图按钮正常或"向上"状态的位图名称。 必需。  
  
 *lpszBitmapResourceSel*  
 指向包含位图的名称，为选定的位图按钮的 null 终止的字符串或"关闭"状态。 可能是**NULL**。  
  
 *lpszBitmapResourceFocus*  
 指向以 null 结尾的字符串，其中包含位图的名称，位图按钮的有针对性的状态。 可能是**NULL**。  
  
 *lpszBitmapResourceDisabled*  
 指向以 null 结尾的字符串，其中包含一个位图按钮已禁用状态的位图的名称。 可能是**NULL**。  
  
 *nIDBitmapResource*  
 指定用于正常情况的位图按钮或"向上"状态的位图资源的资源 ID 号。 必需。  
  
 *nIDBitmapResourceSel*  
 指定位图资源的资源 ID 号，为选定的位图按钮或"关闭"状态。 可能为 0。  
  
 *nIDBitmapResourceFocus*  
 指定位图按钮具有焦点的状态的位图资源的资源 ID 号。 可能为 0。  
  
 *nIDBitmapResourceDisabled*  
 指定位图按钮的禁用状态的位图资源的资源 ID 号。 可能为 0。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&58; 页](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 调用此函数可调整大小为位图的大小的位图按钮。  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&59;](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLTEST](../../visual-cpp-samples.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


