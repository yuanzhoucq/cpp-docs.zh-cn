---
title: "CPen 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- HPEN
- CPen
dev_langs:
- C++
helpviewer_keywords:
- HPEN
- CPen class
- pens, MFC
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
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
ms.openlocfilehash: edea12c84a8f39161acbf367360fd86a1ff19998
ms.lasthandoff: 02/24/2017

---
# <a name="cpen-class"></a>CPen 类
封装一个 Windows 图形设备接口 (GDI) 笔。  
  
## <a name="syntax"></a>语法  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|构造 `CPen` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|创建逻辑修饰或几何笔具有指定的样式、 宽度和画笔属性，并将其附加到`CPen`对象。|  
|[CPen::CreatePenIndirect](#createpenindirect)|创建具有样式、 宽度和颜色中给出的钢笔[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)结构，并将其附加到`CPen`对象。|  
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
  
##  <a name="a-namecpena--cpencpen"></a><a name="cpen"></a>CPen::CPen  
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
 `nPenStyle`  
 指定的笔样式。 此构造函数的第一个版本中的参数可以是下列值之一︰  
  
- **PS_SOLID**创建实心笔。  
  
- **PS_DASH**创建虚线的钢笔。 仅当钢笔的宽度为 1 或更小，设备中的单元时才有效。  
  
- **PS_DOT**创建的以点分隔的钢笔。 仅当钢笔的宽度为 1 或更小，设备中的单元时才有效。  
  
- **PS_DASHDOT**创建具有交替出现的短划线和点的钢笔。 仅当钢笔的宽度为 1 或更小，设备中的单元时才有效。  
  
- **PS_DASHDOTDOT**创建具有交替出现的短划线和双点的钢笔。 仅当钢笔的宽度为 1 或更小，设备中的单元时才有效。  
  
- **PS_NULL**创建 null 钢笔。  
  
- **PS_INSIDEFRAME**创建钢笔绘制由指定的绑定矩形 Windows GDI 输出函数的闭合形状的框架内一条线条 (例如，**椭圆**，**矩形**， `RoundRect`， `Pie`，和`Chord`成员函数)。 该样式用于未指定的绑定矩形的 Windows GDI 输出函数 (例如，`LineTo`成员函数)，框架不受限制的笔在绘图区域。  
  
 第二版`CPen`构造函数指定的类型、 样式、 结束帽和联接属性组合。 应通过使用按位 OR 运算符 (|) 组合中每个类别的值。 笔类型可以是下列值之一︰  
  
- **PS_GEOMETRIC**创建几何钢笔。  
  
- **PS_COSMETIC**创建修饰钢笔。  
  
     第二版`CPen`构造函数将添加的下列笔样式`nPenStyle`:  
  
- **PS_ALTERNATE**创建钢笔设置的每个其他像素。 （这种样式是仅适用于修饰笔）。  
  
- **PS_USERSTYLE**创建使用由用户指定的样式设置数组的钢笔。  
  
     结束帽可以是下列值之一︰  
  
- **PS_ENDCAP_ROUND**端帽是倒圆角。  
  
- **PS_ENDCAP_SQUARE**是方形端帽。  
  
- **PS_ENDCAP_FLAT**端帽是平面。  
  
     联接可以是下列值之一︰  
  
- **PS_JOIN_BEVEL**联接倾斜。  
  
- **PS_JOIN_MITER**联接是斜接时设置的当前限制内[SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076)函数。 如果联接超出此限制，它被倾斜。  
  
- **PS_JOIN_ROUND**联接是倒圆角。  
  
 `nWidth`  
 指定钢笔的宽度。  
  
-   构造函数的第一个版本，如果此值为 0，以设备为单位的宽度始终是 1 个像素，而不考虑映射模式。  
  
-   第二个版本的构造函数中，如果`nPenStyle`是**PS_GEOMETRIC**，宽度提供使用逻辑单位。 如果`nPenStyle`是**PS_COSMETIC**，宽度必须设置为 1。  
  
 `crColor`  
 包含笔 RGB 颜色。  
  
 `pLogBrush`  
 指向`LOGBRUSH`结构。 如果`nPenStyle`是**PS_COSMETIC**、`lbColor`的成员`LOGBRUSH`结构指定笔的颜色和`lbStyle`的成员`LOGBRUSH`结构必须设置为**BS_SOLID**。 如果`nPenStyle`是**PS_GEOMETRIC**，所有成员必须都用于指定笔的画笔属性。  
  
 `nStyleCount`  
 指定的长度，以双字单位`lpStyle`数组。 此值必须为零`nPenStyle`不是**PS_USERSTYLE**。  
  
 `lpStyle`  
 指向双字的值的数组。 第一个值为用户定义的样式中指定的第一个破折号长度，第二个值指定为第一个空格，依次类推的长度。 此指针必须是**NULL**如果`nPenStyle`不是**PS_USERSTYLE**。  
  
### <a name="remarks"></a>备注  
 如果您使用不带任何参数的构造函数，必须初始化生成`CPen`对象`CreatePen`， `CreatePenIndirect`，或`CreateStockObject`成员函数。  
  
 如果您使用不采用参数的构造函数，则没有进一步的初始化是所必需的。 如果遇到错误，而不带任何参数的构造函数将始终会成功，带有参数的构造函数可以引发异常。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&99;](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="a-namecreatepena--cpencreatepen"></a><a name="createpen"></a>CPen::CreatePen  
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
 `nPenStyle`  
 指定为笔的样式。 有关可能的值的列表，请参阅`nPenStyle`中的参数[CPen](#cpen)构造函数。  
  
 `nWidth`  
 指定钢笔的宽度。  
  
-   第一个版本的`CreatePen`，如果此值为 0，以设备为单位的宽度始终是 1 个像素，而不考虑映射模式。  
  
-   第二个版本的`CreatePen`，如果`nPenStyle`是**PS_GEOMETRIC**，宽度提供使用逻辑单位。 如果`nPenStyle`是**PS_COSMETIC**，宽度必须设置为 1。  
  
 `crColor`  
 包含笔 RGB 颜色。  
  
 `pLogBrush`  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)结构。 如果`nPenStyle`是**PS_COSMETIC**、 **lbColor**的成员`LOGBRUSH`结构指定笔的颜色和`lbStyle`的成员`LOGBRUSH`结构必须设置为**BS_SOLID**。 如果**nPenStyle**是**PS_GEOMETRIC**，所有成员必须都用于指定笔的画笔属性。  
  
 `nStyleCount`  
 指定的长度，以双字单位`lpStyle`数组。 此值必须为零`nPenStyle`不是**PS_USERSTYLE**。  
  
 `lpStyle`  
 指向双字的值的数组。 第一个值为用户定义的样式中指定的第一个破折号长度，第二个值指定为第一个空格，依次类推的长度。 此指针必须是**NULL**如果`nPenStyle`不是**PS_USERSTYLE**。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则为零，如果该方法将失败。  
  
### <a name="remarks"></a>备注  
 第一个版本`CreatePen`初始化与指定的样式、 宽度和颜色笔。 可随后将笔选作当前笔针对任何设备上下文。  
  
 宽度大于 1 个像素都应有任何一个的笔**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**样式。  
  
 如果笔有**PS_INSIDEFRAME**样式和不匹配逻辑的颜色表中，一种颜色的颜色笔绘制并用抖色。 **PS_SOLID**笔样式不能用于与抖色创建钢笔。 该样式**PS_INSIDEFRAME**等同于**PS_SOLID**钢笔的宽度是否小于或等于 1。  
  
 第二版`CreatePen`初始化具有指定的样式、 宽度和画笔属性的逻辑修饰或几何笔。 装饰钢笔的宽度始终为 1;几何钢笔的宽度始终指定单位为世界单位。 应用程序创建的逻辑笔后，它可以选择该钢笔入设备上下文通过调用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函数。 笔选入设备上下文后，可以用于绘制直线和曲线。  
  
-   如果`nPenStyle`是**PS_COSMETIC**和**PS_USERSTYLE**中的条目`lpStyle`数组以样式单位指定短划线和空格的长度。 使用钢笔绘制线条的设备由定义样式单元。  
  
-   如果`nPenStyle`是**PS_GEOMETRIC**和**PS_USERSTYLE**中的条目`lpStyle`数组中的逻辑单元指定短划线和空格的长度。  
  
-   如果`nPenStyle`是**PS_ALTERNATE**，样式单元将被忽略，并设置其他每个像素。  
  
 当应用程序不再需要给定的笔时，它应该调用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成员函数或销毁`CPen`对象，以便资源不再使用。 当选中笔时在设备上下文中，应用程序不应删除钢笔。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&100;](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="a-namecreatepenindirecta--cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect  
 初始化具有样式、 宽度和颜色所指向的结构中给出一个笔`lpLogPen`。  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>参数  
 `lpLogPen`  
 指向 Windows [LOGPEN](../../mfc/reference/logpen-structure.md)结构，其中包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 宽度大于 1 个像素都应有任何一个的笔**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**样式。  
  
 如果笔有**PS_INSIDEFRAME**样式和不匹配逻辑的颜色表中，一种颜色的颜色笔绘制并用抖色。 **PS_INSIDEFRAME**样式等同于**PS_SOLID**钢笔的宽度是否小于或等于 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&101;](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="a-namefromhandlea--cpenfromhandle"></a><a name="fromhandle"></a>CPen::FromHandle  
 返回一个指向`CPen`提供给 Windows GDI pen 对象的句柄的对象。  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>参数  
 *hPen*  
 `HPEN`Windows GDI 笔的句柄。  
  
### <a name="return-value"></a>返回值  
 一个指向`CPen`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果 `CPen` 对象未附加到该句柄，则会创建并附加一个临时 `CPen` 对象。 此临时`CPen`对象是否有效，仅直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 换而言之，临时对象才有效的一个窗口消息处理过程。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&105;](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="a-namegetextlogpena--cpengetextlogpen"></a><a name="getextlogpen"></a>CPen::GetExtLogPen  
 获取**EXTLOGPEN**基础结构。  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 `pLogPen`  
 指向[EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)结构，其中包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 **EXTLOGPEN**结构定义样式、 宽度和绘图笔的画笔属性。 例如，调用`GetExtLogPen`以匹配特定样式的笔。  
  
 请参阅中的下列主题[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]笔属性有关的信息︰  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetExtLogPen`来检索钢笔的属性，然后使用相同的颜色中创建新的、 修饰笔。  
  
 [!code-cpp[NVC_MFCDocView #&102;](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="a-namegetlogpena--cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen  
 获取`LOGPEN`基础结构。  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>参数  
 `pLogPen`  
 指向[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)结构，以包含有关笔的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `LOGPEN`结构定义样式、 颜色和绘图笔模式。  
  
 例如，调用`GetLogPen`以匹配特定样式的笔。  
  
 请参阅中的下列主题[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]笔属性有关的信息︰  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>示例  
 下面的代码示例演示如何调用`GetLogPen`来检索一个笔的字符，然后再创建新的实心笔相同的颜色。  
  
 [!code-cpp[NVC_MFCDocView #&103;](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="a-nameoperatorhpena--cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::operator HPEN  
 获取附加的 Windows GDI 句柄`CPen`对象。  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄由表示`CPen`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符被强制转换运算符，它支持直接使用`HPEN`对象。  
  
 有关使用图形对象的详细信息，请参阅文章[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&104;](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBrush 类](../../mfc/reference/cbrush-class.md)

