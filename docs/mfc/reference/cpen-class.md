---
title: CPen 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60fb1c219068cc0c59f908688ea5c471946458ad
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204136"
---
# <a name="cpen-class"></a>CPen 类
封装一个 Windows 图形设备接口 (GDI) 笔。  
  
## <a name="syntax"></a>语法  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|构造 `CPen` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|创建逻辑修饰或几何笔具有指定的样式、 宽度和画笔属性，并将其附加到`CPen`对象。|  
|[CPen::CreatePenIndirect](#createpenindirect)|创建具有样式、 宽度和颜色中给出的钢笔[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)结构，并将其附加到`CPen`对象。|  
|[CPen::FromHandle](#fromhandle)|返回一个指向`CPen`对象在给定 Windows HPEN。|  
|[CPen::GetExtLogPen](#getextlogpen)|获取[EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)基础结构。|  
|[CPen::GetLogPen](#getlogpen)|获取[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)基础结构。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|返回附加到的 Windows 句柄`CPen`对象。|  
  
## <a name="remarks"></a>备注  
 有关使用的详细信息`CPen`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cpen"></a>  CPen::CPen  
 构造 `CPen` 对象。  
  
```  
CPen();

 
CPen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
CPen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 *nPenStyle*  
 指定笔样式。 在构造函数的第一个版本中此参数可以是下列值之一：  
  
- PS_SOLID 创建实心笔。  
  
- PS_DASH 创建虚线的笔。 仅当钢笔的宽度为 1 或更小，在设备中的单元时才有效。  
  
- PS_DOT 创建以点分隔的笔。 仅当钢笔的宽度为 1 或更小，在设备中的单元时才有效。  
  
- 使用替代的笔 PS_DASHDOT 创建短划线和点。 仅当钢笔的宽度为 1 或更小，在设备中的单元时才有效。  
  
- PS_DASHDOTDOT 创建一个使用替代的短划线和双点笔的。 仅当钢笔的宽度为 1 或更小，在设备中的单元时才有效。  
  
- PS_NULL 创建空的笔。  
  
- PS_INSIDEFRAME 通过 Windows GDI 创建钢笔绘制一条线绘制闭合形状的框架内生成输出指定的绑定矩形的函数 (例如， `Ellipse`， `Rectangle`， `RoundRect`， `Pie`，并且`Chord`成员函数)。 此样式用于 Windows GDI 输出函数，没有指定边界矩形时 (例如，`LineTo`成员函数)，框架不受限制的笔绘制的区域。  
  
 第二个版本`CPen`构造函数指定的类型、 样式、 结束帽和联接属性组合。 每个类别中的值应结合使用按位 OR 运算符 (&#124;)。 笔类型可以是下列值之一：  
  
- PS_GEOMETRIC 创建几何笔。  
  
- PS_COSMETIC 创建外观上的笔。  
  
     第二个版本`CPen`构造函数将添加以下笔样式*nPenStyle*:  
  
- PS_ALTERNATE 创建设置的其他每个像素的钢笔。 （此样式。 仅适用于修饰笔）  
  
- PS_USERSTYLE 创建一个使用由用户提供的样式设置数组的笔。  
  
     结束帽可以是下列值之一：  
  
- Round PS_ENDCAP_ROUND 端帽。  
  
- 方形 PS_ENDCAP_SQUARE 端帽。  
  
- PS_ENDCAP_FLAT 端帽是固定的。  
  
     联接可以是下列值之一：  
  
- 被凸凹 PS_JOIN_BEVEL 联接。  
  
- PS_JOIN_MITER 联接是斜时设置的当前限制内[SetMiterLimit](/windows/desktop/api/wingdi/nf-wingdi-setmiterlimit)函数。 如果联接超出此限制，它被凸凹。  
  
- PS_JOIN_ROUND 联接是倒圆角。  
  
 *nWidth*  
 指定笔的宽度。  
  
-   对于构造函数的第一个版本，如果此值为 0，以设备为单位的宽度始终是 1 个像素，而不考虑映射模式。  
  
-   第二个版本的构造函数中，如果*nPenStyle*是 PS_GEOMETRIC，宽度给定逻辑单元中。 如果*nPenStyle*是 PS_COSMETIC，宽度必须设置为 1。  
  
 *crColor*  
 包含笔的 RGB 颜色。  
  
 *pLogBrush*  
 指向`LOGBRUSH`结构。 如果*nPenStyle*是 PS_COSMETIC， *lbColor*的成员`LOGBRUSH`结构指定的钢笔颜色和*lbStyle*隶属`LOGBRUSH`结构必须设置为 BS_SOLID。 如果*nPenStyle*是 PS_GEOMETRIC，所有成员必须都用于指定触笔的画笔属性。  
  
 *nStyleCount*  
 指定的长度，以双字为单位， *lpStyle*数组。 此值必须为零*nPenStyle*不是 PS_USERSTYLE。  
  
 *lpStyle*  
 指向双字的值的数组。 第一个值指定为用户定义的样式中的第一个短划线的长度，则第二个值指定第一个空格和等等的长度。 此指针必须为 NULL，如果*nPenStyle*不是 PS_USERSTYLE。  
  
### <a name="remarks"></a>备注  
 如果你使用不带任何参数的构造函数，则必须初始化生成`CPen`对象使用`CreatePen`， `CreatePenIndirect`，或`CreateStockObject`成员函数。  
  
 如果使用不采用参数的构造函数，没有进一步的初始化是必需的。 如果遇到错误，而不带任何参数的构造函数将始终成功，带有参数的构造函数可以引发异常。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>  CPen::CreatePen  
 创建逻辑修饰或几何笔具有指定的样式、 宽度和画笔属性，并将其附加到`CPen`对象。  
  
```  
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 *nPenStyle*  
 指定笔的样式。 有关可能的值的列表，请参阅*nPenStyle*中的参数[CPen](#cpen)构造函数。  
  
 *nWidth*  
 指定笔的宽度。  
  
-   第一个版本的`CreatePen`，如果此值为 0，以设备为单位的宽度始终为 1 个像素，而不考虑映射模式。  
  
-   第二个版本的`CreatePen`，如果*nPenStyle*是 PS_GEOMETRIC，宽度给定逻辑单元中。 如果*nPenStyle*是 PS_COSMETIC，宽度必须设置为 1。  
  
 *crColor*  
 包含笔的 RGB 颜色。  
  
 *pLogBrush*  
 指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构。 如果*nPenStyle*是 PS_COSMETIC，`lbColor`的成员`LOGBRUSH`结构指定的钢笔颜色并*lbStyle*隶属`LOGBRUSH`结构必须设置为 BS_纯色。 如果 nPenStyle PS_GEOMETRIC，所有成员必须都用于指定触笔的画笔属性。  
  
 *nStyleCount*  
 指定的长度，以双字为单位， *lpStyle*数组。 此值必须为零*nPenStyle*不是 PS_USERSTYLE。  
  
 *lpStyle*  
 指向双字的值的数组。 第一个值指定为用户定义的样式中的第一个短划线的长度，则第二个值指定第一个空格和等等的长度。 此指针必须为 NULL，如果*nPenStyle*不是 PS_USERSTYLE。  
  
### <a name="return-value"></a>返回值  
 如果成功，非零或为零则该方法将失败。  
  
### <a name="remarks"></a>备注  
 第一个版本`CreatePen`初始化使用指定的样式、 宽度和颜色笔。 笔可以随后选择作为当前笔针对任何设备上下文。  
  
 笔的宽度大于 1 个像素都应有 PS_NULL、 PS_SOLID 或 PS_INSIDEFRAME 样式。  
  
 如果笔具有 PS_INSIDEFRAME 样式和颜色的不匹配逻辑的颜色表中的颜色，笔绘制抖色的颜色。 PS_SOLID 笔样式不能用于与抖色创建钢笔。 样式 PS_INSIDEFRAME 等同于 PS_SOLID 钢笔的宽度是否小于或等于 1。  
  
 第二个版本`CreatePen`初始化具有指定的样式、 宽度和画笔属性的逻辑修饰或几何笔。 修饰笔的宽度始终为 1;几何笔的宽度始终指定单位为世界单位。 应用程序可创建逻辑笔后，它可以选择该笔入设备上下文通过调用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函数。 笔选入设备上下文后，它可以用于绘制的直线和曲线。  
  
-   如果*nPenStyle* PS_COSMETIC 和 PS_USERSTYLE 中的条目*lpStyle*数组样式为单位指定短划线和空格的长度。 使用笔绘制一条线的设备定义样式单元。  
  
-   如果*nPenStyle* PS_GEOMETRIC 和 PS_USERSTYLE 中的条目*lpStyle*数组中的逻辑单元指定短划线和空格的长度。  
  
-   如果*nPenStyle*是 PS_ALTERNATE，样式单元将被忽略，并设置其他每个像素。  
  
 当应用程序不再需要给定的笔时，则应调用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数或销毁`CPen`对象，以便资源不再使用。 笔选择在设备上下文中时，应用程序不应删除笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect  
 初始化具有样式、 宽度和颜色提供指向的结构中的笔*lpLogPen*。  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>参数  
 *lpLogPen*  
 指向 Windows [LOGPEN](../../mfc/reference/logpen-structure.md)结构，其中包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 笔的宽度大于 1 个像素都应有 PS_NULL、 PS_SOLID 或 PS_INSIDEFRAME 样式。  
  
 如果笔具有 PS_INSIDEFRAME 样式和颜色的不匹配逻辑的颜色表中的颜色，笔绘制抖色的颜色。 PS_INSIDEFRAME 样式等同于 PS_SOLID 钢笔的宽度是否小于或等于 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>  CPen::FromHandle  
 返回一个指向`CPen`提供给 Windows GDI pen 对象的句柄的对象。  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>参数  
 *hPen*  
 `HPEN` Windows GDI 笔的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CPen`如果成功，否则该值为 NULL 的对象。  
  
### <a name="remarks"></a>备注  
 如果 `CPen` 对象未附加到该句柄，则会创建并附加一个临时 `CPen` 对象。 此临时`CPen`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 换而言之，临时对象才有效的窗口消息处理过程。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>  CPen::GetExtLogPen  
 获取`EXTLOGPEN`基础结构。  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 *pLogPen*  
 指向[EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)结构，其中包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `EXTLOGPEN`结构定义样式、 宽度和钢笔的画笔属性。 例如，调用`GetExtLogPen`以匹配特定样式的笔。  
  
 请参阅适用于笔属性有关的信息的 Windows SDK 中的以下主题：  
  
- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)  
  
- [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)  
  
- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)  
  
- [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetExtLogPen`来检索钢笔的属性，然后使用相同的颜色创建新的修饰的笔。  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>  CPen::GetLogPen  
 获取`LOGPEN`基础结构。  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 *pLogPen*  
 指向[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)结构，以包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `LOGPEN`结构定义样式、 颜色和笔模式。  
  
 例如，调用`GetLogPen`以匹配特定样式的笔。  
  
 请参阅适用于笔属性有关的信息的 Windows SDK 中的以下主题：  
  
- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)  
  
- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetLogPen`来检索笔字符，然后使用相同的颜色创建新的实心笔。  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>  CPen::operator HPEN  
 获取附加的 Windows GDI 句柄的`CPen`对象。  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄由`CPen`对象; 否则为 NULL。  
  
### <a name="remarks"></a>备注  
 此运算符是强制转换运算符，支持直接使用 HPEN 对象。  
  
 有关使用图形对象的详细信息，请参阅文章[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CBrush 类](../../mfc/reference/cbrush-class.md)
