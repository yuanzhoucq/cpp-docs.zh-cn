---
title: CBrush 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs:
- C++
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ffd5e43267ad6a5a462705f410cc1073161ecf0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954099"
---
# <a name="cbrush-class"></a>CBrush 类
封装一个 Windows 图形设备接口 (GDI) 画笔。  
  
## <a name="syntax"></a>语法  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|构造 `CBrush` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化具有样式、 颜色和中指定模式的画笔[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|初始化具有指定独立于设备的位图 (DIB) 模式的画笔。|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化具有指定阴影的模式和颜色的画笔。|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|初始化具有指定位图的模式的画笔。|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化使用指定的纯色画笔。|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|创建一个画笔，它为默认系统颜色。|  
|[CBrush::FromHandle](#fromhandle)|返回一个指向`CBrush`对象提供 Windows 句柄时`HBRUSH`对象。|  
|[CBrush::GetLogBrush](#getlogbrush)|获取[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|返回附加到的 Windows 句柄`CBrush`对象。|  
  
## <a name="remarks"></a>备注  
 若要使用`CBrush`对象，构造`CBrush`对象，并将其传递给任何`CDC`需要画笔的成员函数。  
  
 画笔可以实线、 阴影线，或实现模式化。  
  
 有关详细信息`CBrush`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cbrush"></a>  CBrush::CBrush  
 构造 `CBrush` 对象。  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 *crColor*  
 指定作为 RGB 颜色的画笔的前景色。 如果画笔阴影线，则此参数指定阴影的颜色。  
  
 *nIndex*  
 指定的画笔的阴影样式。 它可以是以下值之一：  
  
- `HS_BDIAGONAL` 在 45 度 （从左到右） 的向下阴影  
  
- `HS_CROSS` 水平和垂直剖面线  
  
- `HS_DIAGCROSS` 在 45 度阴影线  
  
- `HS_FDIAGONAL` 在 45 度 （从左到右） 的向上阴影  
  
- `HS_HORIZONTAL` 水平阴影  
  
- `HS_VERTICAL` 垂直阴影  
  
 *pBitmap*  
 指向`CBitmap`对象，它指定与其画笔绘制的位图。  
  
### <a name="remarks"></a>备注  
 `CBrush` 有四个重载的构造函数。不带任何参数的构造函数构造未经初始化即`CBrush`可以使用它之前必须进行初始化的对象。  
  
 如果你使用不带任何参数的构造函数，必须初始化生成`CBrush`对象[CreateSolidBrush](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果你使用不采用参数的构造函数之一，则没有任何进一步初始化是所必需。 如果遇到错误，而不带任何参数的构造函数将始终会成功，带有参数的构造函数可以引发异常。  
  
 使用单个构造函数[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数构造实心画笔用指定颜色。 颜色指定 RGB 值，并可以使用构造`RGB`WINDOWS 中的宏。H。  
  
 带两个参数的构造函数构造阴影画笔。 *NIndex*参数指定阴影模式的索引。 *CrColor*参数指定的颜色。  
  
 带的构造函数`CBitmap`参数构造图案的画笔。 此参数标识位图。 假定已创建使用位图[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 填充模式中使用的位图的最小大小为 8 个像素的 8 个像素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect  
 初始化具有样式、 颜色和中指定模式的画笔[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>参数  
 *lpLogBrush*  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构，它包含有关画笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 使用当前的文本和背景色绘制字符使用 （1 平面，每个像素的 1 位） 的单色位图创建画笔。 将使用当前的文本色绘制由位设置为 0 的像素。 将当前的背景色绘制由位设置为 1 的像素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush  
 使用独立于设备的位图 (DIB) 指定的模式初始化画笔。  
  
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
 标识包含已打包的独立于设备的位图 (DIB) 的全局内存对象。  
  
 *nUsage*  
 指定是否**bmiColors []** 字段[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)数据结构 （是的"打包 DIB"的一部分） 到当前已实现的逻辑调色板包含显式的 RGB 值或索引。 参数必须是以下值之一：  
  
- **DIB_PAL_COLORS**颜色表包含 16 位索引的数组。  
  
- **DIB_RGB_COLORS**颜色表包含文本的 RGB 值。  
  
 *lpPackedDIB*  
 指向已打包 DIB 组成`BITMAPINFO`紧跟定义位图的像素的字节数组的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可以支持光栅操作任何设备上下文选择画笔。  
  
 在处理 DIB 的方法不同的两个版本：  
  
-   在第一个版本中，若要获取 DIB 的句柄可调用 Windows`GlobalAlloc`函数分配的全局内存块，然后打包 DIB 并用来填充内存。  
  
-   在第二个版本中，它不需要调用`GlobalAlloc`为已打包 DIB 分配内存。  
  
 已打包的 DIB 组成`BITMAPINFO`紧跟定义位图的像素的字节数组的数据结构。 用作填充模式的位图应为 8 个像素 8 个像素。 如果位图大小，则 Windows 将创建使用仅为前 8 行和中与位图左上角的像素的 8 列对应的位的填充模式。  
  
 当应用程序选择两种颜色 DIB 模式画笔入单色设备上下文时，Windows 将忽略指定的颜色中 DIB，并改为显示使用的设备上下文的当前文本和背景颜色的模式画笔。 映射到第一种颜色 （在 DIB 颜色表中的偏移量 0） 的 DIB 的像素为单位显示使用的文本颜色。 映射到的第二个颜色 （在颜色表中的偏移量 1） 的像素为单位显示使用的背景色。  
  
 有关使用以下 Windows 功能的信息，请参阅 Windows SDK:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (此函数提供仅为对于早于 3.0 版本的 Windows 编写的应用程序的兼容性的; 使用`CreateDIBPatternBrushPt`函数。)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) （此函数应使用基于 Win32 的应用程序。）  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush  
 初始化具有指定阴影的模式和颜色的画笔。  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 指定的画笔的阴影样式。 它可以是以下值之一：  
  
- `HS_BDIAGONAL` 在 45 度 （从左到右） 的向下阴影  
  
- `HS_CROSS` 水平和垂直剖面线  
  
- `HS_DIAGCROSS` 在 45 度阴影线  
  
- `HS_FDIAGONAL` 在 45 度 （从左到右） 的向上阴影  
  
- `HS_HORIZONTAL` 水平阴影  
  
- `HS_VERTICAL` 垂直阴影  
  
 *crColor*  
 指定作为 RGB 颜色 （阴影的颜色） 的画笔的前景色。 请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)适用于详细信息的 Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush  
 初始化具有指定位图的模式的画笔。  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 *pBitmap*  
 标识位图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可以支持光栅操作任何设备上下文选择画笔。 由标识位图*pBitmap*通常通过使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函数。  
  
 用作填充模式的位图应为 8 个像素 8 个像素。 如果位图大小，则 Windows 将只使用对应的前 8 行和列中与位图左上角的像素的位。  
  
 模式画笔可以删除而不会影响相关联的位图。 这意味着位图可以用于创建任意数量的模式画笔。  
  
 使用当前的文本和背景色绘制字符使用单色位图 （1 颜色平面，每个像素的 1 位） 创建画笔。 使用当前的文本色绘制由位设置为 0 的像素为单位。 使用当前的背景色绘制由位设置为 1 的像素为单位。  
  
 有关使用信息[CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508)，Windows 函数中，请参阅 Windows SDK。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush  
 初始化使用指定纯色画笔。  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 *crColor*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)结构，它指定的画笔的颜色。 颜色指定 RGB 值，并可以使用 WINDOWS 中的 RGB 宏构造。H。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 当应用程序已完成使用创建的画笔`CreateSolidBrush`，它应选择设备上下文中的画笔。  
  
### <a name="example"></a>示例  
  请参阅示例[CBrush::CBrush](#cbrush)。  
  
##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush  
 初始化画笔的颜色。  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 指定颜色索引。 此值对应于用来绘制一个 21 窗口元素的颜色。 请参阅[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) Windows SDK for 的值列表中。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 画笔随后可以选择作为任何设备上下文的当前画笔。  
  
 当应用程序已完成使用创建的画笔`CreateSysColorBrush`，它应选择设备上下文中的画笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>  CBrush::FromHandle  
 返回一个指向`CBrush`对象提供 Windows 句柄时[HBRUSH](#operator_hbrush)对象。  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>参数  
 *hBrush*  
 `HANDLE` 为 Windows GDI 画笔。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CBrush`对象成功; 否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CBrush`对象尚未附加到该句柄，一种临时`CBrush`创建对象并将其附加。 此临时`CBrush`对象仅在应用程序必须在其事件循环中的空闲时间的下一步时间是否有效。 在此期间，将删除所有临时的图形对象。 换而言之，仅在一个窗口消息处理期间临时对象有效。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CBrush::CBrush](#cbrush)。  
  
##  <a name="getlogbrush"></a>  CBrush::GetLogBrush  
 调用此成员函数可检索`LOGBRUSH`结构。  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>参数  
 *pLogBrush*  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构，它包含有关画笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，和*pLogBrush*是有效的指针，则返回值是存储到缓冲区的字节数。  
  
 如果函数成功，和*pLogBrush*是**NULL**，返回值是保存该函数的信息所需的字节数应将存储到缓冲区。  
  
 如果函数失败，返回值为 0。  
  
### <a name="remarks"></a>备注  
 `LOGBRUSH`结构定义样式、 颜色和模式的画笔。  
  
 例如，调用`GetLogBrush`特定颜色或位图模式相匹配。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH  
 此运算符用于获取附加的 Windows GDI 句柄的`CBrush`对象。  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄表示`CBrush`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符是一个强制转换运算符，它支持直接使用`HBRUSH`对象。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap 类](../../mfc/reference/cbitmap-class.md)   
 [CDC 类](../../mfc/reference/cdc-class.md)
