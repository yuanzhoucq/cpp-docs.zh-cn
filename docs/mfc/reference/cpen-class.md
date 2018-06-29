---
title: CPen 类 |Microsoft 文档
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
ms.openlocfilehash: 17337239a3a58a0283fc96eadcd4417c3d5c69b0
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079585"
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
|[CPen::CreatePen](#createpen)|创建具有指定的样式、 宽度和画笔属性的逻辑的外观或几何钢笔和将其附加到`CPen`对象。|  
|[CPen::CreatePenIndirect](#createpenindirect)|创建具有样式、 宽度和颜色中给定的钢笔[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)结构，以及是否将其附加到`CPen`对象。|  
|[CPen::FromHandle](#fromhandle)|返回一个指向`CPen`对象在给定 Windows `HPEN`。|  
|[CPen::GetExtLogPen](#getextlogpen)|获取[EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)基础结构。|  
|[CPen::GetLogPen](#getlogpen)|获取[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)基础结构。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|返回附加到的 Windows 句柄`CPen`对象。|  
  
## <a name="remarks"></a>备注  
 有关详细信息使用`CPen`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
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
 指定的钢笔样式。 此构造函数的第一个版本中的参数可以是下列值之一：  
  
- **PS_SOLID**创建实心钢笔。  
  
- **PS_DASH**创建虚线的钢笔。 仅当钢笔的宽度为 1 个或更少，设备中单位时才有效。  
  
- **PS_DOT**创建的以点分隔的钢笔。 仅当钢笔的宽度为 1 个或更少，设备中单位时才有效。  
  
- **PS_DASHDOT**创建具有交替短划线和点的钢笔。 仅当钢笔的宽度为 1 个或更少，设备中单位时才有效。  
  
- **PS_DASHDOTDOT**创建具有交替短划线和双点的钢笔。 仅当钢笔的宽度为 1 个或更少，设备中单位时才有效。  
  
- **PS_NULL**创建 null 钢笔。  
  
- **PS_INSIDEFRAME**创建钢笔绘制由指定边界的矩形的 Windows GDI 输出函数的闭合形状的框架内的行 (例如， `Ellipse`， `Rectangle`， `RoundRect`， `Pie`，和`Chord`成员函数)。 此样式用于 Windows GDI 输出函数，没有指定边界的矩形 (例如，`LineTo`成员函数)，钢笔的绘图区域时不受限制的帧。  
  
 第二个版本`CPen`构造函数指定的类型、 样式、 端帽和联接属性的组合。 应使用按位 OR 运算符组合中每个类别的值 (&#124;)。 钢笔类型可以是下列值之一：  
  
- **PS_GEOMETRIC**创建几何钢笔。  
  
- **PS_COSMETIC**创建修饰钢笔。  
  
     第二个版本`CPen`构造函数将添加以下钢笔样式*nPenStyle*:  
  
- **PS_ALTERNATE**创建钢笔设置每个其他像素。 （此样式是仅适用于修饰钢笔。）  
  
- **PS_USERSTYLE**创建使用样式数组由用户提供钢笔。  
  
     端帽可以是以下值之一：  
  
- **PS_ENDCAP_ROUND**端帽将舍入。  
  
- **PS_ENDCAP_SQUARE**端帽是正方形。  
  
- **PS_ENDCAP_FLAT**端帽是平面。  
  
     联接可以是以下值之一：  
  
- **PS_JOIN_BEVEL**联接倾斜。  
  
- **PS_JOIN_MITER**联接是斜接时设置的当前限制内[SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076)函数。 如果联接超出此限制，它被倾斜。  
  
- **PS_JOIN_ROUND**联接是舍入。  
  
 *nWidth*  
 指定的笔宽。  
  
-   对于构造函数的第一个版本，如果此值为 0，以设备为单位的宽度始终是 1 个像素，而不管映射模式如何。  
  
-   第二个版本的构造函数中，如果*nPenStyle*是**PS_GEOMETRIC**，宽度给定逻辑单位。 如果*nPenStyle*是**PS_COSMETIC**，宽度必须设置为 1。  
  
 *crColor*  
 包含为笔 RGB 颜色。  
  
 *pLogBrush*  
 指向`LOGBRUSH`结构。 如果*nPenStyle*是**PS_COSMETIC**、 *lbColor*的成员`LOGBRUSH`结构指定的颜色的笔和*lbStyle*的成员`LOGBRUSH`结构必须设置为**BS_SOLID**。 如果*nPenStyle*是**PS_GEOMETRIC**，所有成员必须都用于指定钢笔的画笔属性。  
  
 *nStyleCount*  
 指定的长度，以双字单位*lpStyle*数组。 此值必须为零*nPenStyle*不**PS_USERSTYLE**。  
  
 *lpStyle*  
 指向双字的值的数组。 第一个值为用户定义的样式中指定的第一个破折号长度，第二个值指定的第一个空格和等等的长度。 此指针必须是**NULL**如果*nPenStyle*不**PS_USERSTYLE**。  
  
### <a name="remarks"></a>备注  
 如果你使用不带任何参数的构造函数，必须初始化生成`CPen`对象`CreatePen`， `CreatePenIndirect`，或`CreateStockObject`成员函数。  
  
 如果你使用不采用参数的构造函数，没有进一步的初始化是必需的。 如果遇到错误，而不带任何参数的构造函数将始终会成功，带自变量的构造函数可以引发异常。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>  CPen::CreatePen  
 创建具有指定的样式、 宽度和画笔属性的逻辑的外观或几何钢笔和将其附加到`CPen`对象。  
  
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
 指定为笔的样式。 有关可能的值的列表，请参阅*nPenStyle*中的参数[CPen](#cpen)构造函数。  
  
 *nWidth*  
 指定的笔宽。  
  
-   第一个版本的`CreatePen`，如果此值为 0，以设备为单位的宽度始终为 1 个像素，无论映射模式如何。  
  
-   第二个版本的`CreatePen`，如果*nPenStyle*是**PS_GEOMETRIC**，宽度给定逻辑单位。 如果*nPenStyle*是**PS_COSMETIC**，宽度必须设置为 1。  
  
 *crColor*  
 包含为笔 RGB 颜色。  
  
 *pLogBrush*  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。 如果*nPenStyle*是**PS_COSMETIC**、 **lbColor**的成员`LOGBRUSH`结构指定的颜色的笔和*lbStyle*的成员`LOGBRUSH`结构必须设置为**BS_SOLID**。 如果**nPenStyle**是**PS_GEOMETRIC**，所有成员必须都用于指定钢笔的画笔属性。  
  
 *nStyleCount*  
 指定的长度，以双字单位*lpStyle*数组。 此值必须为零*nPenStyle*不**PS_USERSTYLE**。  
  
 *lpStyle*  
 指向双字的值的数组。 第一个值为用户定义的样式中指定的第一个破折号长度，第二个值指定的第一个空格和等等的长度。 此指针必须是**NULL**如果*nPenStyle*不**PS_USERSTYLE**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为非 0 或为零则该方法将失败。  
  
### <a name="remarks"></a>备注  
 第一个版本`CreatePen`初始化使用指定的样式、 宽度和颜色笔。 钢笔可以随后选择作为任何设备上下文的当前笔。  
  
 大于 1 个像素应始终具有宽度的钢笔**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**样式。  
  
 如果钢笔具有**PS_INSIDEFRAME**样式和不匹配逻辑的颜色表中，一种颜色的颜色钢笔绘制抖色的颜色。 **PS_SOLID**笔样式不能用于创建钢笔具有抖色。 样式**PS_INSIDEFRAME**等同于**PS_SOLID**钢笔的宽度是否小于或等于 1。  
  
 第二个版本`CreatePen`初始化具有指定的样式，宽度，，画笔属性的逻辑修饰或几何笔。 修饰钢笔的宽度始终为 1;始终在世界单位中指定几何笔宽。 应用程序创建一个逻辑笔后，它可以选择该钢笔入设备上下文通过调用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函数。 钢笔选入设备上下文之后，它可以用于绘制直线和曲线。  
  
-   如果*nPenStyle*是**PS_COSMETIC**和**PS_USERSTYLE**中的条目*lpStyle*数组指定短划线和中的空格的长度样式单位。 使用钢笔绘制线条的设备由定义样式单元。  
  
-   如果*nPenStyle*是**PS_GEOMETRIC**和**PS_USERSTYLE**中的条目*lpStyle*数组指定短划线和中的空格的长度逻辑单元。  
  
-   如果*nPenStyle*是**PS_ALTERNATE**，忽略样式单元，并设置其他每个像素。  
  
 当应用程序不再需要给定的钢笔时，则应调用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数或销毁`CPen`对象，以便资源不再使用。 钢笔选择在设备上下文中时，应用程序不应删除钢笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect  
 初始化具有样式、 宽度和颜色中指向的结构提供钢笔*lpLogPen*。  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>参数  
 *lpLogPen*  
 指向 Windows [LOGPEN](../../mfc/reference/logpen-structure.md)结构，它包含有关钢笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 大于 1 个像素应始终具有宽度的钢笔**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**样式。  
  
 如果钢笔具有**PS_INSIDEFRAME**样式和不匹配逻辑的颜色表中，一种颜色的颜色钢笔绘制抖色的颜色。 **PS_INSIDEFRAME**样式等同于**PS_SOLID**钢笔的宽度是否小于或等于 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>  CPen::FromHandle  
 返回一个指向`CPen`提供 Windows GDI pen 对象的句柄的对象。  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>参数  
 *hPen*  
 `HPEN` Windows GDI 钢笔的句柄。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CPen`对象成功; 否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果 `CPen` 对象未附加到该句柄，则会创建并附加一个临时 `CPen` 对象。 此临时`CPen`对象是否有效，仅在下次应用程序在其事件循环中具有空闲时间，直到在哪些时间所有临时图形对象会被删除。 换而言之，临时对象才有效一个窗口消息处理的过程。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>  CPen::GetExtLogPen  
 获取**EXTLOGPEN**基础结构。  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 *pLogPen*  
 指向[EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)结构，它包含有关钢笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 **EXTLOGPEN**结构定义样式、 宽度和钢笔的画笔属性。 例如，调用`GetExtLogPen`以匹配钢笔的特定样式。  
  
 请参阅 Windows SDK for 笔属性有关的信息中的以下主题：  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetExtLogPen`以检索钢笔的属性，然后再创建一个新的修饰笔相同的颜色。  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>  CPen::GetLogPen  
 获取`LOGPEN`基础结构。  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 *pLogPen*  
 指向[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)结构，以包含有关钢笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `LOGPEN`结构定义样式、 颜色和钢笔的模式。  
  
 例如，调用`GetLogPen`以匹配钢笔的特定样式。  
  
 请参阅 Windows SDK for 笔属性有关的信息中的以下主题：  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetLogPen`检索并将钢笔字符，然后使用相同的颜色中创建新的稳定钢笔。  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>  CPen::operator HPEN  
 获取附加的 Windows GDI 句柄的`CPen`对象。  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄表示`CPen`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符是一个强制转换运算符，它支持直接使用`HPEN`对象。  
  
 有关使用图形对象的详细信息，请参阅文章[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBrush 类](../../mfc/reference/cbrush-class.md)
