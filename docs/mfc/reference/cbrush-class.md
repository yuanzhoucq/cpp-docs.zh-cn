---
title: "CBrush 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBrush
dev_langs:
- C++
helpviewer_keywords:
- brushes, CBrush class
- CBrush class
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: efcbe2757de3a7e4621e2b20c88726ead111cf8c
ms.lasthandoff: 02/24/2017

---
# <a name="cbrush-class"></a>CBrush 类
封装一个 Windows 图形设备接口 (GDI) 画笔。  
  
## <a name="syntax"></a>语法  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|构造 `CBrush` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化具有样式、 颜色和模式中指定的画笔[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|与设备无关位图 (DIB) 所指定的模式初始化画笔。|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化具有指定阴影的模式和颜色的画笔。|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|初始化画笔的位图指定的模式。|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化具有指定实色的画笔。|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|创建一个画笔，它为默认系统颜色。|  
|[CBrush::FromHandle](#fromhandle)|返回一个指向`CBrush`对象时给出到了 Windows 句柄`HBRUSH`对象。|  
|[CBrush::GetLogBrush](#getlogbrush)|获取[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|返回附加到的 Windows 句柄`CBrush`对象。|  
  
## <a name="remarks"></a>备注  
 若要使用`CBrush`对象，请构造`CBrush`对象，并将其传递给任何`CDC`需要画笔的成员函数。  
  
 画笔可以实线、 印记，或图案。  
  
 有关详细信息`CBrush`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecbrusha--cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush  
 构造 `CBrush` 对象。  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定为 RGB 颜色的画笔的前景色。 如果影线画笔，此参数指定阴影的颜色。  
  
 `nIndex`  
 指定画笔的阴影样式。 它可以是下列值之一︰  
  
- `HS_BDIAGONAL`为 45 度 （从左到右） 的向下阴影  
  
- `HS_CROSS`水平和垂直交叉影线  
  
- `HS_DIAGCROSS`45 度交叉影线  
  
- `HS_FDIAGONAL`向上阴影 （从左到右） 设为 45 度  
  
- `HS_HORIZONTAL`水平阴影  
  
- `HS_VERTICAL`垂直阴影  
  
 `pBitmap`  
 指向`CBitmap`对象，它指定与画笔绘制的位图。  
  
### <a name="remarks"></a>备注  
 `CBrush`具有四个重载构造函数。不带任何参数的构造函数构造未初始化`CBrush`必须进行初始化，然后才能使用的对象。  
  
 如果您使用不带任何参数的构造函数，必须初始化生成`CBrush`对象[CreateSolidBrush](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果您使用不采用参数的构造函数之一，则无需初始化是所必需。 如果遇到错误，而不带任何参数的构造函数将始终会成功，带有参数的构造函数可以引发异常。  
  
 使用单个构造函数[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数构造实心画笔用指定颜色。 颜色指定 RGB 值，并可以利用构造`RGB`WINDOWS 中的宏。H。  
  
 带有两个参数的构造函数构造阴影画笔。 `nIndex`参数指定的索引的阴影模式。 `crColor`参数指定的颜色。  
  
 使用构造函数`CBitmap`参数构造模式的画笔。 此参数用于标识位图。 假定已创建使用位图[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 位图来填充模式中使用的最小大小为 8 x 8 像素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&21;](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="a-namecreatebrushindirecta--cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect  
 初始化具有样式、 颜色和模式中指定的画笔[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>参数  
 *lpLogBrush*  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构，其中包含有关画笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 使用当前的文本和背景颜色绘制字符使用 （1 平面） 1 位 / 像素的单色位图创建画笔。 将使用当前的文本颜色绘制像素为单位表示的位设置为 0。 将当前的背景色绘制像素为单位表示的位设置为 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&22;](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="a-namecreatedibpatternbrusha--cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush  
 与设备无关位图 (DIB) 所指定的模式初始化画笔。  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>参数  
 *hPackedDIB*  
 标识一个全局内存对象，包含已打包的设备无关位图 (DIB)。  
  
 *nUsage*  
 指定是否**bmiColors []**字段[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)数据结构 （是的"打包 DIB"的一部分） 到当前已实现的逻辑调色板包含显式 RGB 值或索引。 参数必须为下列值之一︰  
  
- **DIB_PAL_COLORS**颜色表包含 16 位索引的数组。  
  
- **DIB_RGB_COLORS**颜色表包含文本的 RGB 值。  
  
 *lpPackedDIB*  
 指向已打包 DIB 组成`BITMAPINFO`紧跟定义位图的像素的字节数组的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可为任何支持光栅操作的设备上下文被选择画笔。  
  
 在两个版本处理 DIB 的方式的不同之处︰  
  
-   在第一个版本中，若要获取 DIB 的句柄您调用 Windows **GlobalAlloc**函数分配的全局内存块，然后用已打包 DIB 填充内存。  
  
-   在第二个版本中，它不需要调用**GlobalAlloc**分配内存来存放打包 DIB。  
  
 已打包的 DIB 组成`BITMAPINFO`紧跟定义位图的像素的字节数组的数据结构。 位图用作填充模式应为 8 x 8 像素。 如果位图大于，Windows 将创建使用只有对应于前 8 行和 8 个列中与位图左上角的像素位的填充模式。  
  
 当应用程序选择两种颜色 DIB 图案画笔入单色设备上下文时，Windows 将忽略在 DIB 中指定的颜色，并改为显示使用设备上下文的当前文本和背景色的模式画笔。 使用的文本颜色来显示像素映射到第一种颜色 （按 DIB 颜色表中的偏移量 0） 的 DIB。 使用背景色显示映射到 （按颜色表中的偏移量 1） 的第二个颜色的像素为单位。  
  
 有关使用以下 Windows 功能的信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (仅为与 Windows 的版本早于 3.0 编写的应用程序兼容性提供此函数; 使用**CreateDIBPatternBrushPt**函数。)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) （此函数应基于 Win32 的应用程序。）  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView 第&23;](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="a-namecreatehatchbrusha--cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CreateHatchBrush  
 初始化具有指定阴影的模式和颜色的画笔。  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定画笔的阴影样式。 它可以是下列值之一︰  
  
- `HS_BDIAGONAL`为 45 度 （从左到右） 的向下阴影  
  
- `HS_CROSS`水平和垂直交叉影线  
  
- `HS_DIAGCROSS`45 度交叉影线  
  
- `HS_FDIAGONAL`向上阴影 （从左到右） 设为 45 度  
  
- `HS_HORIZONTAL`水平阴影  
  
- `HS_VERTICAL`垂直阴影  
  
 `crColor`  
 指定为 RGB 颜色 （阴影的颜色） 的背景色的画笔。 请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&24;](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="a-namecreatepatternbrusha--cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush  
 初始化画笔的位图指定的模式。  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 `pBitmap`  
 标识一个位图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可为任何支持光栅操作的设备上下文被选择画笔。 由标识位图`pBitmap`通常通过使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函数。  
  
 位图用作填充模式应为 8 x 8 像素。 如果位图大于，Windows 将只使用对应的前 8 行和列中与位图左上角的像素的位。  
  
 图案画笔可以删除而不会影响相关联的位图。 这意味着位图可用来创建任意数量的图案画笔。  
  
 使用当前的文本和背景颜色绘制字符使用单色位图 （1 颜色平面，1 位 / 像素） 创建的画笔。 使用当前的文本颜色绘制像素为单位表示的位设置为 0。 当前的背景色绘制像素为单位表示的位设置为 1。  
  
 有关使用[CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508)，Windows 函数，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&25;](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="a-namecreatesolidbrusha--cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CreateSolidBrush  
 初始化具有指定实色的画笔。  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，它指定画笔的颜色。 颜色指定 RGB 值，并可以利用构造`RGB`WINDOWS 中的宏。H。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 当应用程序已完成使用由创建画笔`CreateSolidBrush`，它应选择从设备上下文画笔。  
  
### <a name="example"></a>示例  
  请参阅示例[CBrush::CBrush](#cbrush)。  
  
##  <a name="a-namecreatesyscolorbrusha--cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush  
 初始化画笔颜色。  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定颜色索引。 此值对应于用来绘制一个 21 窗口元素的颜色。 请参阅[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 当应用程序已完成使用由创建画笔`CreateSysColorBrush`，它应选择从设备上下文画笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&26;](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="a-namefromhandlea--cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle  
 返回一个指向`CBrush`对象时给出到了 Windows 句柄[HBRUSH](#operator_hbrush)对象。  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>参数  
 `hBrush`  
 `HANDLE`为 Windows GDI 画笔。  
  
### <a name="return-value"></a>返回值  
 一个指向`CBrush`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CBrush`对象尚未附加到该句柄，一种临时`CBrush`创建对象并将其连接。 此临时`CBrush`对象是否有效，直到下一步该应用程序在其事件循环内有空闲时间。 此时，将删除所有临时图形对象。 换而言之，仅在一个窗口消息的处理过程的临时对象有效。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CBrush::CBrush](#cbrush)。  
  
##  <a name="a-namegetlogbrusha--cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush  
 调用此成员函数以检索`LOGBRUSH`结构。  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>参数  
 `pLogBrush`  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构，其中包含有关画笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，和`pLogBrush`是有效的指针，则返回值是存储到缓冲区的字节数。  
  
 如果函数成功，和`pLogBrush`是**NULL**，则返回值是包含该函数的信息所需的字节数将存储到缓冲区。  
  
 如果函数失败，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 `LOGBRUSH`结构定义样式、 颜色和画笔的模式。  
  
 例如，调用`GetLogBrush`特定颜色或位图的模式相匹配。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&27;](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="a-nameoperatorhbrusha--cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operator HBRUSH  
 使用此运算符将获得附加的 Windows GDI 句柄的`CBrush`对象。  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄由表示`CBrush`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符被强制转换运算符，它支持直接使用`HBRUSH`对象。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&28;](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap 类](../../mfc/reference/cbitmap-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)

