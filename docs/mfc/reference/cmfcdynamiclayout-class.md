---
title: "CMFCDynamicLayout 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
dev_langs: C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 29b161d889aefc55e818a16233212a55bdcb45de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout 类
指定窗口中的控件如何随着用户重设窗口大小而移动和重设大小。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|构造 `CMFCDynamicLayout` 对象。|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cmfcdynamiclayout:: Additem](#additem)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|  
|[Cmfcdynamiclayout:: Adjust](#adjust)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|  
|[CMFCDynamicLayout::Create](#create)|存储并验证主机窗口。|  
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|返回指向主机窗口的指针。|  
|[CMFCDynamicLayout::GetMinSize](#getminsize)|返回窗口大小，低于此大小则不调整布局。|  
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|检索窗口的当前工作区的矩形。|  
|[Cmfcdynamiclayout:: Hasitem](#hasitem)|检查子控件是否已添加到动态布局。|  
|[Cmfcdynamiclayout:: Isempty](#isempty)|检查动态布局是否未添加任何子窗口。|  
|[CMFCDynamicLayout::LoadResource](#loadresource)|从 AFX_DIALOG_LAYOUT 资源读取动态布局，然后将该布局应用到主机窗口。|  
|静态[cmfcdynamiclayout:: Movehorizontal](#movehorizontal)|获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时水平移动多少子控件。|  
|静态[cmfcdynamiclayout:: Movehorizontalandvertical](#movehorizontalandvertical)|获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时水平移动多少子控件。|  
|静态[cmfcdynamiclayout:: Movenone](#movenone)|获取[MoveSettings](#movesettings_structure)表示不移动，垂直或水平，子控件的值。|  
|静态[cmfcdynamiclayout:: Movevertical](#movevertical)|获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时垂直移动多少子控件。|  
|[CMFCDynamicLayout::SetMinSize](#setminsize)|设置窗口大小，低于此大小则不调整布局。|  
|静态[cmfcdynamiclayout:: Sizehorizontal](#sizehorizontal)|获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时水平调整多少子控件。|  
|静态[cmfcdynamiclayout:: Sizehorizontalandvertical](#sizehorizontalandvertical)|获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时水平调整多少子控件。|  
|静态[cmfcdynamiclayout:: Sizenone](#sizenone)|获取[SizeSettings](#sizesettings_structure)值，该值表示子控件的大小不会更改。|  
|静态[cmfcdynamiclayout:: Sizevertical](#sizevertical)|获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时垂直调整多少子控件。|  
  
## <a name="nested-types"></a>嵌套类型  
  
|名称|描述|  
|----------|-----------------|  
|[Cmfcdynamiclayout:: Movesettings 结构](#movesettings_structure)|封装动态布局中控件的移动数据。|  
|[Cmfcdynamiclayout:: Sizesettings 结构](#sizesettings_structure)|封装动态布局中控件的大小更改数据。|  
  
## <a name="remarks"></a>备注  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxlayout.h  
  
##  <a name="additem"></a>Cmfcdynamiclayout:: Additem  
 将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。  
  
```  
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

 
BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```  
  
### <a name="parameters"></a>参数  
 `hwnd`  
 要添加的窗口句柄。  
  
 `nID`  
 要添加的子控件 ID。  
  
 `moveSettings`  
 描述控件如何随窗口大小的更改而移动的结构。  
  
 `sizeSettings`  
 描述控件如何随窗口大小的更改而调整大小的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功添加了项，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 调整承载窗口的大小时，子控件的位置和大小会动态更改。  
  
##  <a name="adjust"></a>Cmfcdynamiclayout:: Adjust  
 将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。  
  
```  
void Adjust();
```  
  
### <a name="remarks"></a>备注  
 调整承载窗口的大小时，子控件的位置和大小会动态更改。  
  
##  <a name="create"></a>CMFCDynamicLayout::Create  
 存储并验证主机窗口。  
  
```  
BOOL Create(CWnd* pHostWnd);
```  
  
### <a name="parameters"></a>参数  
 pHostWnd  
 指向主机窗口的指针。  
  
### <a name="return-value"></a>返回值  
 如果创建成功，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd  
 返回指向主机窗口的指针。  
  
```  
CWnd* GetHostWnd();
```  
  
### <a name="return-value"></a>返回值  
 指向主机窗口的指针。  
  
### <a name="remarks"></a>备注  
 默认情况下，参照此窗口重新计算所有子控件的位置。  
  
##  <a name="getminsize"></a>CMFCDynamicLayout::GetMinSize  
 返回窗口大小，低于此大小则不调整布局。  
  
```  
CSize GetMinSize();
```  
  
### <a name="return-value"></a>返回值  
 窗口大小，低于此大小则不调整布局。  
  
### <a name="remarks"></a>备注  
 调整承载窗口的大小时，子控件的位置和大小会动态更改，但存在一个最低大小，低于此大小则不调整布局。 用户可将窗口大小调整为较小，但届时窗口的某些部分将隐藏。  
  
##  <a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect  
 检索窗口的当前工作区的矩形。  
  
```  
void GetHostWndRect(CRect& rect,);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 函数返回后，此参数将包含布局区域的边框。 这是一个 out 参数；输入的值将被覆盖。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasitem"></a>Cmfcdynamiclayout:: Hasitem  
 检查子控件是否已添加到动态布局。  
  
```  
BOOL HasItem(HWND hwnd);
```  
  
### <a name="parameters"></a>参数  
 `hwnd`  
 控件的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 如果布局已有此项，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isempty"></a>Cmfcdynamiclayout:: Isempty  
 检查动态布局是否未添加任何子窗口。  
  
```  
BOOL IsEmpty();
```  
  
### <a name="return-value"></a>返回值  
 如果布局没有任何项，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="loadresource"></a>CMFCDynamicLayout::LoadResource  
 从 AFX_DIALOG_LAYOUT 资源读取动态布局，然后将该布局应用到主机窗口。  
  
```  
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);  
```  
  
### <a name="parameters"></a>参数  
 `pHostWnd`  
 指向主机窗口的指针。  
  
 `lpResource`  
 指向包含 AFX_DIALOG_LAYOUT 资源的缓冲区的指针。  
  
 `dwSize`  
 缓冲区大小（以字节为单位）。  
  
### <a name="return-value"></a>返回值  
 如果已加载资源并将其应用于主机窗口，则为 TRUE；否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="movehorizontal"></a>Cmfcdynamiclayout:: Movehorizontal  
 获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时水平移动多少子控件。  
  
```  
static MoveSettings MoveHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nRatio`  
 以百分比形式定义在用户调整承载窗口大小时水平移动子控件的距离。  
  
### <a name="return-value"></a>返回值  
 A [MoveSettings](#movesettings_structure)值，该值封装请求的移动比率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="movehorizontalandvertical"></a>Cmfcdynamiclayout:: Movehorizontalandvertical  
 获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时水平移动多少子控件。  
  
```  
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nXRatio`  
 以百分比形式定义在用户调整承载窗口大小时水平移动子控件的距离。  
  
 `nYRatio`  
 以百分比形式定义在用户调整承载窗口大小时垂直移动子控件的距离。  
  
### <a name="return-value"></a>返回值  
 A [MoveSettings](#movesettings_structure)值，该值封装请求的移动比率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="movenone"></a>Cmfcdynamiclayout:: Movenone  
 获取[MoveSettings](#movesettings_structure)表示不移动，垂直或水平，子控件的值。  
  
```  
static MoveSettings MoveNone();  
```  
  
### <a name="return-value"></a>返回值  
 A [MoveSettings](#movesettings_structure)到位，修复控件，以便它不随用户调整承载窗口大小时的值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="movesettings_structure"></a>Cmfcdynamiclayout:: Movesettings 结构  
 封装动态布局中控件的移动数据。  
  
```  
struct CMFCDynamicLayout::MoveSettings;  
```  
  
### <a name="remarks"></a>备注  
 这是嵌套在 `CMFCDynamicLayout` 内的类。  

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal
检查移动数据是否指定非零的垂直移动。  
  

```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `MoveSettings` 对象指定一个非零的水平移动，则为 TRUE。  

 ## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone
 检查移动数据是否指定无移动。  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `MoveSettings` 对象指定无移动，则为 TRUE。  

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical
  请检查移动数据是否指定非零的垂直移动。  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `MoveSettings` 对象指定非零的垂直移动，则为 true。  

##  <a name="movevertical"></a>Cmfcdynamiclayout:: Movevertical  
 获取[MoveSettings](#movesettings_structure)值，该值定义当用户调整其承载窗口大小时垂直移动多少子控件。  
  
```  
static MoveSettings MoveVertical(int nRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nRatio`  
 以百分比形式定义在用户调整承载窗口大小时垂直移动子控件的距离。  
  
### <a name="return-value"></a>返回值  
 A [MoveSettings](#movesettings_structure)值，该值封装请求的移动比率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setminsize"></a>CMFCDynamicLayout::SetMinSize  
 设置窗口大小，低于此大小则不调整布局。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 所需大小，低于此大小则不调整布局。  
  
### <a name="remarks"></a>备注  
 调整承载窗口的大小时，子控件的位置和大小会动态更改，但存在一个最低大小，低于此大小则不调整布局。 用户可将窗口大小调整为较小，但届时窗口的某些部分将隐藏。  
  
##  <a name="sizehorizontal"></a>Cmfcdynamiclayout:: Sizehorizontal  
 获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时水平调整多少子控件。  
  
```  
static SizeSettings SizeHorizontal(int nRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nRatio`  
 以百分比形式定义在用户调整承载窗口大小时水平调整子控件的程度。  
  
### <a name="return-value"></a>返回值  
 A [SizeSettings](#sizesettings_structure)值，该值封装请求的大小比率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizehorizontalandvertical"></a>Cmfcdynamiclayout:: Sizehorizontalandvertical  
 获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时水平调整多少子控件。  
  
```  
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nXRatio`  
 以百分比形式定义在用户调整承载窗口大小时水平调整子控件的程度。  
  
 `nYRatio`  
 以百分比形式定义在用户调整承载窗口大小时垂直调整子控件的距离。  
  
### <a name="return-value"></a>返回值  
 A [SizeSettings](#sizesettings_structure)值，该值封装请求的大小比率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizenone"></a>Cmfcdynamiclayout:: Sizenone  
 获取[SizeSettings](#sizesettings_structure)值，该值表示子控件的大小不会更改。  
  
```  
static SizeSettings SizeNone();  
```  
  
### <a name="return-value"></a>返回值  
 A [SizeSettings](#sizesettings_structure)值，该值控制在特定大小，以便它不会更改大小，当用户调整承载窗口大小时。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizesettings_structure"></a>Cmfcdynamiclayout:: Sizesettings 结构  
 封装动态布局中控件的大小更改数据。  
  
```  
struct CMFCDynamicLayout::SizeSettings;  
```  
  
### <a name="remarks"></a>备注  
 这是嵌套在 `CMFCDynamicLayout` 内的类。  

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal
检查大小调整数据是否指定非零水平大小调整。  
  
```  
BOOL IsHorizontal() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `SizeSettings` 对象指定非零的水平大小调整，则为 TRUE。 

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone
检查大小调整数据是否不指定大小调整。  
  
```  
BOOL IsNone() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `SizeSettings` 对象指定不重设大小，则为 true。  

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical
检查大小调整数据是否指定非零垂直大小调整。  
  
```  
BOOL IsVertical() const 
```  
  
## <a name="return-value"></a>返回值  
 如果 `SizeSettings` 对象指定非零的垂直大小调整，则为 TRUE。  

##  <a name="sizevertical"></a>Cmfcdynamiclayout:: Sizevertical  
 获取[SizeSettings](#sizesettings_structure)值，该值定义当用户调整其承载窗口大小时垂直调整多少子控件。  
  
```  
static SizeSettings SizeVertical(int nRatio);  
```  
  
### <a name="parameters"></a>参数  
 `nRatio`  
 以百分比形式定义在用户调整承载窗口大小时垂直调整子控件的距离。  
  
### <a name="return-value"></a>返回值  
 A [SizeSettings](#sizesettings_structure)值，该值封装请求的大小比率。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
