---
title: "CFont 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFont
dev_langs:
- C++
helpviewer_keywords:
- CFont class
- GDI, font classes
- fonts, MFC classes
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
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
ms.openlocfilehash: cc7ecfb850bf24013acdb55075eeb3d64d4994ee
ms.lasthandoff: 02/24/2017

---
# <a name="cfont-class"></a>CFont 类
封装一个 Windows 图形设备接口 (GDI) 字体并提供用于操作字体的成员函数。  
  
## <a name="syntax"></a>语法  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|构造 `CFont` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|初始化`CFont`的具有指定特性。|  
|[Cfont:: Createfontindirect](#createfontindirect)|初始化`CFont`对象中给出的特征`LOGFONT`结构。|  
|[CFont::CreatePointFont](#createpointfont)|初始化`CFont`与指定的高度，测量以十分之一点和字样。|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|与相同`CreateFontIndirect`只不过字体高度的单位十分之一点而不是逻辑单元。|  
|[CFont::FromHandle](#fromhandle)|返回一个指向`CFont`对象在给定 Windows **HFONT**。|  
|[CFont::GetLogFont](#getlogfont)|填充`LOGFONT`提供有关连接到的逻辑字体信息`CFont`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|返回 Windows GDI 字体句柄附加到`CFont`对象。|  
  
## <a name="remarks"></a>备注  
 若要使用`CFont`对象，请构造`CFont`对象，并附加到其与 Windows 字体[CreateFont](#createfont)， [CreateFontIndirect](#createfontindirect)， [CreatePointFont](#createpointfont)，或[CreatePointFontIndirect](#createpointfontindirect)，然后使用该对象的成员函数以操作该字体。  
  
 `CreatePointFont`和`CreatePointFontIndirect`函数通常可以更轻松地使用比`CreateFont`或`CreateFontIndirect`由于它们自动进行转换的高度的字体磅值从到逻辑单元。  
  
 有关详细信息`CFont`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecfonta--cfontcfont"></a><a name="cfont"></a>CFont::CFont  
 构造 `CFont` 对象。  
  
```  
CFont();
```  
  
### <a name="remarks"></a>备注  
 生成的对象必须用初始化`CreateFont`， `CreateFontIndirect`， `CreatePointFont`，或`CreatePointFontIndirect`然后才能使用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&70;](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="a-namecreatefonta--cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont  
 初始化`CFont`具有指定特征的对象。  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>参数  
 `nHeight`  
 指定字体的所需的高度 （以逻辑单位）。 请参阅`lfHeight`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关的说明。 数值的绝对值`nHeight`转换后不能超过 16384 设备单位。 对于所有高度比较，字体映射程序看起来不超过所请求的大小的最大字体或最小字号如果所有字体都超过所请求的大小。  
  
 `nWidth`  
 指定的字体中字符的平均宽度 （以逻辑单位）。 如果`nWidth`为 0，则将针对要查找由差的绝对值的数值的最接近的可用字体数字化纵横比匹配设备的纵横比。  
  
 `nEscapement`  
 指定之间行距向量和显示器表面的 x 轴的角度 （以 0.1 度为单位）。 行距向量是通过这些来源行上的第一个和最后一个字符的行。 角度是从 x 轴按逆时针方向测量的。 请参阅`lfEscapement`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
 `nOrientation`  
 指定字符的基线和 x 轴之间的角度 （以 0.1 度为单位）。 角度是从用于坐标系统中 y 方向是向下和从 y 方向是最多的坐标系统为 x 轴沿顺时针方向的 x 轴按逆时针方向测量的。  
  
 `nWeight`  
 指定的字体粗细 （以每 1000 个，绘制像素为单位）。 请参阅`lfWeight`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。 所述的数值是近似的;实际的外观取决于字样。 一些字体只有`FW_NORMAL`， `FW_REGULAR`，和`FW_BOLD`权重。 如果`FW_DONTCARE`指定，则使用默认权重。  
  
 `bItalic`  
 指定字体为斜体。  
  
 `bUnderline`  
 指定的字体加下划线。  
  
 `cStrikeOut`  
 指定字体中的字符冒。 如果指定删除线字体设置为非零值。  
  
 `nCharSet`  
 指定的字体字符 setSee`lfCharSet`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
 OEM 字符集与系统相关。  
  
 在系统中可能存在与其他字符集的字体。 使用一种字体具有未知的字符集的应用程序不能尝试转换或解释要使用该字体呈现的字符串。 相反，应直接向输出设备驱动程序传递字符串。  
  
 字体映射器不使用`DEFAULT_CHARSET`值。 应用程序可以使用此值允许的名称和一种字体能够完整地描述逻辑字体大小。 如果不存在具有指定名称的字体，则可以将任何字符集中的字体替换为指定的字体。 若要避免意外的结果，应用程序应使用`DEFAULT_CHARSET`谨慎值。  
  
 `nOutPrecision`  
 指定所需的输出精度。 输出精度定义所请求的字体高度、 宽度、 字符方向、 行距和音调输出必须匹配程度。 请参阅`lfOutPrecision`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值和详细信息的列表。  
  
 `nClipPrecision`  
 指定所需的剪辑精度。 剪辑精度定义如何剪辑的一部分位于的剪辑区域之外的字符。 请参阅`lfClipPrecision`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
 若要使用的嵌入的只读的字体，应用程序必须指定`CLIP_ENCAPSULATE`。  
  
 若要实现一致的设备、 TrueType、 和矢量字体旋转，应用程序可以使用或运算符组合`CLIP_LH_ANGLES`值与任何其他`nClipPrecision`值。 如果`CLIP_LH_ANGLES`设置位的所有字体旋转取决于坐标系统的方向是惯用左手还是惯用右手。 (有关坐标系统的方向的详细信息，请参阅的说明`nOrientation`参数。)如果`CLIP_LH_ANGLES`是未设置，设备字体始终旋转逆时针旋转，但其他字体的旋转所依赖的坐标系统的方向。  
  
 `nQuality`  
 指定字体的输出质量，它定义如何仔细 GDI 必须尝试匹配与实际的物理字体的逻辑字体属性。 请参阅`lfQuality`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
 `nPitchAndFamily`  
 指定的间距和字体系列。 请参阅`lfPitchAndFamily`中的成员`LOGFONT`结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值和详细信息的列表。  
  
 `lpszFacename`  
 一个`CString`或以 null 结尾的字符串，指定的字体的字体名称的指针。 此字符串的长度不得超过 30 个字符。 Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619)函数可用于枚举所有当前可用的字体。 如果`lpszFacename`是`NULL`，GDI 使用独立于设备的字样。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可以为针对任何设备上下文的字体选择字体。  
  
 `CreateFont`函数不会创建一个新的 Windows GDI 字体。 它只是选择最接近的匹配从可用的物理字体到 GDI。  
  
 创建一个逻辑字体时，应用程序可以为大多数参数使用默认设置。 应始终提供特定值的参数是`nHeight`和`lpszFacename`。 如果`nHeight`和`lpszFacename`未设置应用程序创建的逻辑字体与设备相关。  
  
 在使用完`CFont`创建的对象`CreateFont`函数，请使用`CDC::SelectObject`若要选择到设备上下文的另一种字体，然后删除`CFont`不再需要的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&71;](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="a-namecreatefontindirecta--cfontcreatefontindirect"></a><a name="createfontindirect"></a>Cfont:: Createfontindirect  
 初始化`CFont`对象中给出的特征[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>参数  
 `lpLogFont`  
 指向`LOGFONT`结构，它定义的逻辑字体特征。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 随后可以作为任何设备的当前字体选择字体。  
  
 此字体已在指定的特征[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。 通过选择字体时[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)成员函数，GDI 字体映射器将尝试匹配与现有的物理字体的逻辑字体。 如果字体映射程序未能找到完全匹配的逻辑字体，它提供了其特征与尽可能多的尽可能所请求的特性的可选字体。  
  
 当您不再需要`CFont`创建的对象`CreateFontIndirect`函数，请使用`CDC::SelectObject`若要选择到设备上下文的另一种字体，然后删除`CFont`不再需要的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&72;](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="a-namecreatepointfonta--cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont  
 此函数提供一种简单方法创建指定的字体的字体和磅值。  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nPointSize`  
 请求的字体高度，以十分之一一个点。 （例如，传递 120 请求 12 磅字体）。  
  
 `lpszFaceName`  
 一个`CString`或以 null 结尾的字符串，指定的字体的字体名称的指针。 此字符串的长度不得超过 30 个字符。 Windows **EnumFontFamilies**函数可用于枚举所有当前可用的字体。 如果`lpszFaceName`是**NULL**，GDI 使用独立于设备的字样。  
  
 `pDC`  
 指向[CDC](../../mfc/reference/cdc-class.md)对象可用于将转换的高度以`nPointSize`到逻辑单元。 如果**NULL**，屏幕设备上下文用于进行转换。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 会自动将转换的高度以`nPointSize`到使用的逻辑单元`CDC`指向对象`pDC`。  
  
 在使用完`CFont`创建的对象`CreatePointFont`函数，第一次选择从设备上下文的字体，然后删除`CFont`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&73;](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="a-namecreatepointfontindirecta--cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 此函数相当于[CreateFontIndirect](#createfontindirect)只不过**lfHeight**的成员`LOGFONT`解释以十分之一地点的点，而不是设备的设备。  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpLogFont`  
 指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构，它定义的逻辑字体特征。 **LfHeight**的成员`LOGFONT`结构大小的单位十分之一点而不是逻辑单元。 (例如，设置**lfHeight**为 120 请求 12 磅字体。)  
  
 `pDC`  
 指向[CDC](../../mfc/reference/cdc-class.md)对象可用于将转换的高度以**lfHeight**到逻辑单元。 如果**NULL**，屏幕设备上下文用于进行转换。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数会自动将转换的高度以**lfHeight**到使用的逻辑单元`CDC`指向对象`pDC`之前传递`LOGFONT`到 Windows 的结构。  
  
 在使用完`CFont`创建的对象`CreatePointFontIndirect`函数，第一次选择从设备上下文的字体，然后删除`CFont`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&74;](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="a-namefromhandlea--cfontfromhandle"></a><a name="fromhandle"></a>CFont::FromHandle  
 返回一个指向`CFont`对象在给定**HFONT** Windows GDI 字体对象的句柄。  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>参数  
 `hFont`  
 **HFONT** Windows 字体的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CFont`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CFont`对象尚未附加到该句柄，一种临时`CFont`创建对象并将其连接。 此临时`CFont`对象是否有效，仅直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 另一种说法是仅在一个窗口消息的处理过程的临时对象有效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&75;](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="a-namegetlogfonta--cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont  
 调用此函数可检索的副本`LOGFONT`结构`CFont`。  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>参数  
 *pLogFont*  
 指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)接收字体信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，否则为 0，非零值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&76;](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="a-nameoperatorhfonta--cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::operator HFONT  
 此运算符用于获取附加到的字体的 Windows GDI 句柄`CFont`对象。  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>返回值  
 Windows GDI 字体对象的句柄附加到`CFont`如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 由于此运算符自动用于从转换`CFont`到[字体和文本](http://msdn.microsoft.com/library/windows/desktop/dd144819)，您可以将传递`CFont`对象传递给函数的预期**HFONT**s。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&77;](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




