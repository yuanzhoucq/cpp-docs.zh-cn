---
title: "CPalette 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
dev_langs:
- C++
helpviewer_keywords:
- CPalette class
- HPALETTE
- color palettes, MFC
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
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
ms.openlocfilehash: 6ccd389eaf765993c59311cc1041893f2cf9fbfa
ms.lasthandoff: 02/24/2017

---
# <a name="cpalette-class"></a>CPalette 类
封装一个 Windows 调色板。  
  
## <a name="syntax"></a>语法  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|构造`CPalette`对象没有附加的 Windows 调色板。 必须初始化`CPalette`对象与其中一个成员函数的初始化然后才能使用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cpalette:: Animatepalette](#animatepalette)|替换由逻辑调色板中的条目`CPalette`对象。 应用程序不必更新其工作区，因为 Windows 立即将映射到系统调色板的新条目。|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|创建设备上下文的半色调调色板，并将其附加到`CPalette`对象。|  
|[CPalette::CreatePalette](#createpalette)|创建一个 Windows 调色板，并将其附加到`CPalette`对象。|  
|[CPalette::FromHandle](#fromhandle)|返回一个指向`CPalette`对象时提供给 Windows 调色板对象的句柄。|  
|[CPalette::GetEntryCount](#getentrycount)|检索逻辑调色板中的调色板条目数。|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|在与最接近的颜色值的逻辑调色板中返回的项的索引。|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|检索调色板逻辑调色板中的项的范围。|  
|[CPalette::ResizePalette](#resizepalette)|更改由指定的逻辑调色板大小`CPalette`对象传递给指定的条目数。|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|设置逻辑调色板中的条目范围中的 RGB 颜色值和标志。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|返回`HPALETTE`附加到`CPalette`。|  
  
## <a name="remarks"></a>备注  
 调色板提供应用程序的颜色输出设备 （如显示设备） 之间的接口。 该接口允许应用程序以充分利用输出设备的颜色功能而不会造成严重影响其他应用程序显示的颜色。 Windows 使用应用程序的逻辑调色板 （所需颜色的列表） 和系统调色板 （它定义可用的颜色） 来确定使用的颜色。  
  
 一个`CPalette`对象提供了成员函数，为操作调色板引用的对象。 构造`CPalette`对象，并使用其成员函数来创建实际的调色板中，图形设备接口 (GDI) 对象，并处理其项和其他属性。  
  
 有关详细信息使用`CPalette`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="animatepalette"></a>Cpalette:: Animatepalette  
 替换附加到的逻辑调色板中的条目`CPalette`对象。  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>参数  
 `nStartIndex`  
 指定要进行动画处理的调色板中的第一个条目。  
  
 `nNumEntries`  
 指定要进行动画处理的调色板中的条目数。  
  
 `lpPaletteColors`  
 指向数组的第一个成员[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)结构，以替换由标识调色板条目`nStartIndex`和`nNumEntries`。  
  
### <a name="remarks"></a>备注  
 在应用程序调用`AnimatePalette`，它没有以更新其工作区，因为 Windows 立即将映射到系统调色板的新条目。  
  
 `AnimatePalette`函数将仅更改带有条目**PC_RESERVED**标志在相应的设置**palPaletteEntry**的成员[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)附加到的结构`CPalette`对象。 请参阅**LOGPALETTE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关此结构的详细信息。  
  
##  <a name="cpalette"></a>CPalette::CPalette  
 构造 `CPalette` 对象。  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>备注  
 该对象具有没有附加的调色板，直到您调用`CreatePalette`以附加一个。  
  
##  <a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette  
 创建设备上下文的半色调调色板。  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 标识设备上下文。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序应创建设备上下文的拉伸模式设置为半色调调色板**半色调**。 返回由逻辑半色调调色板[CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503)成员函数应然后选择并意识到之前在设备上下文[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[StretchDIBits](http://msdn.microsoft.com/library/windows/desktop/dd145121)调用函数。  
  
 请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息`CreateHalftonePalette`和**StretchDIBits**。  
  
##  <a name="createpalette"></a>CPalette::CreatePalette  
 初始化`CPalette`对象通过创建一个 Windows 逻辑调色板并将其附加到`CPalette`对象。  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>参数  
 `lpLogPalette`  
 指向[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)结构，其中包含有关逻辑调色板中的颜色的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息**LOGPALETTE**结构。  
  
##  <a name="fromhandle"></a>CPalette::FromHandle  
 返回一个指向`CPalette`对象时提供给 Windows 调色板对象的句柄。  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>参数  
 `hPalette`  
 指向 Windows GDI 调色板的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CPalette`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CPalette`对象尚未附加到 Windows 调色板，临时`CPalette`创建对象并将其连接。 此临时`CPalette`对象是否有效，仅直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 换而言之，仅在一个窗口消息的处理过程的临时对象有效。  
  
##  <a name="getentrycount"></a>CPalette::GetEntryCount  
 调用此成员函数可检索给定的逻辑调色板中的条目数。  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>返回值  
 逻辑调色板中的条目数。  
  
##  <a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex  
 在与指定的颜色值最接近的逻辑调色板中返回的项的索引。  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定要匹配的颜色。  
  
### <a name="return-value"></a>返回值  
 逻辑调色板中的项索引。 一项包含与指定的颜色最近似匹配的颜色。  
  
##  <a name="getpaletteentries"></a>CPalette::GetPaletteEntries  
 检索调色板逻辑调色板中的项的范围。  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>参数  
 `nStartIndex`  
 指定要检索的逻辑调色板中的第一个条目。  
  
 `nNumEntries`  
 指定要检索的逻辑调色板中的条目数。  
  
 `lpPaletteColors`  
 指向数组的[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)数据结构，以接收调色板条目。 该数组必须包含至少尽可能多的数据结构按照`nNumEntries`。  
  
### <a name="return-value"></a>返回值  
 从逻辑调色板; 中检索的条目数如果函数失败，则为 0。  
  
##  <a name="operator_hpalette"></a>CPalette::operator HPALETTE  
 使用此运算符将获得附加的 Windows GDI 句柄的`CPalette`对象。  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄由表示`CPalette`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符被强制转换运算符，它支持直接使用`HPALETTE`对象。  
  
 有关使用图形对象的详细信息，请参阅文章[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="resizepalette"></a>CPalette::ResizePalette  
 附加到的逻辑调色板的大小更改`CPalette`对象传递给由指定的条目数`nNumEntries`。  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>参数  
 `nNumEntries`  
 它具有调整大小后，调色板中指定的条目数。  
  
### <a name="return-value"></a>返回值  
 调色板已成功地调整大小; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果应用程序调用`ResizePalette`以缩减的调色板，调整调色板中剩余的条目保持不变。 如果在应用程序调用`ResizePalette`要放大调色板，附加调色板条目已设置为黑色 （红色、 绿色和蓝色值是全部由 0），并且所有其他项的标志设置为 0。  
  
 有关详细信息 Windows API `ResizePalette`，请参阅[ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setpaletteentries"></a>CPalette::SetPaletteEntries  
 设置逻辑调色板中的条目范围中的 RGB 颜色值和标志。  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>参数  
 `nStartIndex`  
 指定要设置的逻辑调色板中的第一个条目。  
  
 `nNumEntries`  
 指定要设置的逻辑调色板中的条目数。  
  
 `lpPaletteColors`  
 指向数组的[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)数据结构，以接收调色板条目。 该数组必须包含至少尽可能多的数据结构按照`nNumEntries`。  
  
### <a name="return-value"></a>返回值  
 设置逻辑调色板; 中的条目数如果函数失败，则为 0。  
  
### <a name="remarks"></a>备注  
 如果逻辑调色板选入设备上下文中，当应用程序调用`SetPaletteEntries`，所做的更改才会生效之前应用程序将调用[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)。  
  
 有关详细信息的 Windows 结构**PALETTEENTRY**，请参阅[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 DIBLOOK](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)




