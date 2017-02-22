---
title: "CRect 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPCRECT 数据类型"
  - "CRect 类"
  - "LPRECT 运算符"
  - "RECT 结构"
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRect 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类似于 Windows [RECT](../../mfc/reference/rect-structure1.md) 结构。  
  
## <a name="syntax"></a>语法  
  
```  
class CRect : public tagRECT  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRect::CRect](#crect__crect)|构造 `CRect` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRect::BottomRight](#crect__bottomright)|返回的右下角点 `CRect`。|  
|[CRect::CenterPoint](#crect__centerpoint)|返回的中心点 `CRect`。|  
|[CRect::CopyRect](#crect__copyrect)|将复制的源矩形的尺寸 `CRect`。|  
|[CRect::DeflateRect](#crect__deflaterect)|减小的宽度和高度 `CRect`。|  
|[CRect::EqualRect](#crect__equalrect)|确定是否 `CRect` 是否等同于给定的矩形。|  
|[CRect::Height](#crect__height)|计算的高度 `CRect`。|  
|[CRect::InflateRect](#crect__inflaterect)|增加宽度和高度 `CRect`。|  
|[CRect::IntersectRect](#crect__intersectrect)|集 `CRect` 等于两个矩形交集。|  
|[CRect::IsRectEmpty](#crect__isrectempty)|确定是否 `CRect` 为空。 `CRect` 如果，为空的宽度和/或高度均为 0。|  
|[CRect::IsRectNull](#crect__isrectnull)|确定是否 **顶部**, ，**底部**, ，**左**, ，和 **右侧** 成员变量都是平等为 0。|  
|[CRect::MoveToX](#crect__movetox)|将移动 `CRect` 到指定的 x 坐标。|  
|[CRect::MoveToXY](#crect__movetoxy)|将移动 `CRect` 指定到 x 和 y 坐标。|  
|[CRect::MoveToY](#crect__movetoy)|将移动 `CRect` 到指定的 y 坐标。|  
|[Crect:: Normalizerect](#crect__normalizerect)|标准化的高度和宽度 `CRect`。|  
|[CRect::OffsetRect](#crect__offsetrect)|将移动 `CRect` 由指定的偏移量。|  
|[CRect::PtInRect](#crect__ptinrect)|确定指定的点是否位于内 `CRect`。|  
|[CRect::SetRect](#crect__setrect)|设置的尺寸 `CRect`。|  
|[CRect::SetRectEmpty](#crect__setrectempty)|集 `CRect` 到 （所有坐标都等于为 0） 为空矩形。|  
|[CRect::Size](#crect__size)|计算的大小 `CRect`。|  
|[CRect::SubtractRect](#crect__subtractrect)|向量中减去从另一个矩形。|  
|[CRect::TopLeft](#crect__topleft)|返回的左上角点 `CRect`。|  
|[CRect::UnionRect](#crect__unionrect)|集 `CRect` 等于两个矩形的并集。|  
|[CRect::Width](#crect__width)|计算的宽度 `CRect`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CRect::operator-](#crect__operator_-)|从给定的偏移量中减去 `CRect` 或压缩 `CRect` ，并返回结果 `CRect`。|  
|[CRect::operator LPCRECT](#crect__operator_lpcrect)|将转换 `CRect` 到 **LPCRECT**。|  
|[CRect::operator LPRECT](#crect__operator_lprect)|将转换 `CRect` 到 `LPRECT`。|  
|[CRect::operator ！ =](#crect__operator__neq)|确定是否 `CRect` 不等同于一个矩形。|  
|[CRect::operator &amp;](#crect__operator__amp_)|创建的交集 `CRect` 和一个矩形，并返回结果 `CRect`。|  
|[CRect::operator &amp;=](#crect__operator__amp__eq)|集 `CRect` 相等的交集 `CRect` 和一个矩形。|  
|[CRect::operator |](#crect__operator__or)|创建的并集 `CRect` 和一个矩形，并返回结果 `CRect`。|  
|[CRect::operator |=](#crect__operator__or_eq)|集 `CRect` 等于的并集 `CRect` 和一个矩形。|  
|[CRect::operator +](#crect__operator__add)|将添加到给定的偏移量 `CRect` 或放大 `CRect` ，并返回结果 `CRect`。|  
|[CRect::operator + =](#crect__operator__add_eq)|将添加到指定的偏移量 `CRect` 或放大 `CRect`。|  
|[CRect::operator =](#crect__operator__eq)|将复制到一个矩形的尺寸 `CRect`。|  
|[CRect::operator =](#crect__operator_-_eq)|从指定的偏移量中减去 `CRect` 或压缩 `CRect`。|  
|[CRect::operator = =](#crect__operator__eq_eq)|确定是否 `CRect` 是否等同于一个矩形。|  
  
## <a name="remarks"></a>备注  
 `CRect` 此外包括成员函数以操作 `CRect` 对象和 Windows `RECT` 结构。  
  
 一个 `CRect` 对象可以作为函数参数传递的任何位置 `RECT` 结构， **LPCRECT**, ，或 `LPRECT` 可以传递。  
  
> [!NOTE]
>  此类派生自 **tagRECT** 结构。 (名称 **tagRECT** 是很少通常使用名称 `RECT` 结构。)这意味着，数据成员 ( **左**, ，**顶部**, ，**右侧**, ，和 **底部**) 的 `RECT` 结构不是可访问的数据成员的 `CRect`。  
  
 一个 `CRect` 包含定义的矩形的左上角和右下角的点的成员变量。  
  
 指定时 `CRect`, ，您必须小心以构造它，以便将其具体化，— 换句话说，这样的左坐标的值是否小于右侧和顶端小于底部。 例如，左上角 (10,10)，并定义一个规范化的矩形，右下方 (20,20)，但左上角 (20,20)，右下方 (10,10) 定义一个非规范化的矩形。 如果该矩形不会加以规范，许多 `CRect` 成员函数可能会返回不正确的结果。 (请参阅 [Crect:: Normalizerect](#crect__normalizerect) 有关这些函数的列表。)在调用需要规范化的矩形的函数之前，你可以通过调用规范化非规范化矩形 `NormalizeRect` 函数。  
  
 执行操作时要格外小心 `CRect` 与 [CDC::DPtoLP] (.../Topic/CDC%20Class.md#cdc__dptolp 和 [CDC::LPtoDP] (.../Topic/CDC%20Class.md#cdc__lptodp 成员函数。 如果显示上下文的映射模式，则这样 y 范围为负，如下所示 `MM_LOENGLISH`, ，然后 `CDC::DPtoLP` 将转换 `CRect` ，以便其顶部大于底部。 函数如 **高度** 和 **大小** 然后将返回负数值的已转换的高度 `CRect`, ，并且该矩形将非规范化。  
  
 使用重载 `CRect` 运算符，第一个操作数必须是 `CRect`; 第二个可以是 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象。  
  
> [!NOTE]
>  有关详细信息共享实用程序类 (如 `CRect`)，请参阅 [共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>要求  
 **标头︰** atltypes.h  
  
##  <a name="a-namecrectbottomrighta-crectbottomright"></a><a name="crect__bottomright"></a>  CRect::BottomRight  
 作为引用返回坐标 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 中包含的对象 `CRect`。  
  
```  
 
CPoint& BottomRight() throw();

const CPoint& BottomRight() const throw();

 
```  
  
### <a name="return-value"></a>返回值  
 该矩形右下角的坐标。  
  
### <a name="remarks"></a>备注  
 此函数可用于获取或设置的矩形的右下角。 设置通过使用此函数在赋值运算符的左侧角。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#35](../../atl-mfc-shared/codesnippet/CPP/crect-class_1.cpp)]  
  
##  <a name="a-namecrectcenterpointa-crectcenterpoint"></a><a name="crect__centerpoint"></a>  CRect::CenterPoint  
 计算的中心点 `CRect` 通过加上向左和右值并除以两个，并添加顶部和底部值除以两个。  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>返回值  
 一个 `CPoint` 对象，它的中心点 `CRect`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#36](../../atl-mfc-shared/codesnippet/CPP/crect-class_2.cpp)]  
  
##  <a name="a-namecrectcopyrecta-crectcopyrect"></a><a name="crect__copyrect"></a>  CRect::CopyRect  
 副本 `lpSrcRect` 到矩形 `CRect`。  
  
```  
 
void CopyRect(
LPCRECT   
lpSrcRect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `lpSrcRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 要复制的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#37](../../atl-mfc-shared/codesnippet/CPP/crect-class_3.cpp)]  
  
##  <a name="a-namecrectcrecta-crectcrect"></a><a name="crect__crect"></a>  CRect::CRect  
 构造 `CRect` 对象。  
  
```  
 
    CRect() throw();
CRect(
 int    
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();
CRect(
 const RECT& 
    srcRect) throw();
CRect(
 LPCRECT    
    lpSrcRect) throw();
CRect(
 POINT    
    point ,  
    SIZE 
    size) throw();
CRect(
 POINT    
    topLeft ,  
    POINT 
    bottomRight) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *l*  
 指定的左侧的位置 `CRect`。  
  
 *t*  
 指定顶部 `CRect`。  
  
 *r*  
 指定的正确位置 `CRect`。  
  
 *b*  
 指定底部 `CRect`。  
  
 *srcRect*  
 是指 [RECT](../../mfc/reference/rect-structure1.md) 具有实体的坐标，结构 `CRect`。  
  
 `lpSrcRect`  
 指向 `RECT` 具有实体的坐标，结构 `CRect`。  
  
 `point`  
 指定要构造的矩形的起始点。 对应于左上角。  
  
 `size`  
 指定的位移从左上角到右下角要构造的矩形。  
  
 *左边框*  
 指定的左上角位置 `CRect`。  
  
 *bottomRight*  
 指定的右下角位置 `CRect`。  
  
### <a name="remarks"></a>备注  
 如果未提供参数， **左**, ，**顶部**, ，**右侧**, ，和 **底部** 成员未初始化。  
  
  `CRect`( **RECT const &**) 和 `CRect`( **LPCRECT**) 构造函数执行 [CopyRect](#crect__copyrect)。 其他构造函数直接初始化的对象的成员变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#38](../../atl-mfc-shared/codesnippet/CPP/crect-class_4.cpp)]  
  
##  <a name="a-namecrectdeflaterecta-crectdeflaterect"></a><a name="crect__deflaterect"></a>  CRect::DeflateRect  
 `DeflateRect` 压缩 `CRect` 通过向其中心移动侧面。  
  
```  
 
    void DeflateRect(
    int 
    x ,  
    int 
    y) throw();
void DeflateRect(
    SIZE 
    size) throw();
void DeflateRect(
    LPCRECT 
    lpRect) throw();
void DeflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要 deflate 左侧的单位数和右侧的 `CRect`。  
  
 *y*  
 指定要 deflate 顶部和底部的单位数 `CRect`。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 或 [CSize](../../atl-mfc-shared/reference/csize-class.md) ，它指定要 deflate 的单位数量 `CRect`。  `cx` 值指定要 deflate 左侧和右侧的单位数和 `cy` 值指定要 deflate 顶部和底部的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` ，它指定要 deflate 每一侧的单位数。  
  
 *l*  
 指定要 deflate 的左侧的单位数 `CRect`。  
  
 *t*  
 指定要 deflate 顶部的单位数 `CRect`。  
  
 *r*  
 指定要 deflate 右侧的单位数 `CRect`。  
  
 *b*  
 指定要 deflate 底部的单位数 `CRect`。  
  
### <a name="remarks"></a>备注  
 若要这样做， `DeflateRect` 将单元添加至 left 和 top，减去单位从右侧和底部。 参数 `DeflateRect` 进行了签名值; 正值 deflate `CRect` 和负值放大量它。  
  
 前两个重载 deflate 的另一侧这两个对 `CRect` ，以便按两次减少其总宽度 *x* (或 `cx`) 和按两次减少其总高度 *y* (或 `cy`)。 其他两个重载 deflate 的每一侧 `CRect` 相互独立地。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#39](../../atl-mfc-shared/codesnippet/CPP/crect-class_5.cpp)]  
  
##  <a name="a-namecrectequalrecta-crectequalrect"></a><a name="crect__equalrect"></a>  CRect::EqualRect  
 确定是否 `CRect` 是否等同于给定的矩形。  
  
```  
 
BOOL EqualRect(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含一个矩形的左上角和右下角坐标。  
  
### <a name="return-value"></a>返回值  
 非零，如果两个矩形具有相同的顶部、 左边框、 下、 和正确的值;否则为 0。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#40](../../atl-mfc-shared/codesnippet/CPP/crect-class_6.cpp)]  
  
##  <a name="a-namecrectheighta-crectheight"></a><a name="crect__height"></a>  CRect::Height  
 计算的高度 `CRect` 通过减去从最低值位于顶部的值。  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>返回值  
 高度 `CRect`。  
  
### <a name="remarks"></a>备注  
 所得到的值可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#41](../../atl-mfc-shared/codesnippet/CPP/crect-class_7.cpp)]  
  
##  <a name="a-namecrectinflaterecta-crectinflaterect"></a><a name="crect__inflaterect"></a>  CRect::InflateRect  
 `InflateRect` 放大 `CRect` 通过侧面抛弃其中心。  
  
```  
 
    void InflateRect(
    int 
    x ,  
    int 
    y) throw();
void InflateRect(
    SIZE 
    size) throw();
void InflateRect(
    LPCRECT 
    lpRect) throw();
void InflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要放大量左侧的单位数和右侧的 `CRect`。  
  
 *y*  
 指定要放大量顶部和底部的单位数 `CRect`。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 或 [CSize](../../atl-mfc-shared/reference/csize-class.md) ，它指定要放大量的单位数量 `CRect`。  `cx` 值指定要放大量左侧和右侧的单位数和 `cy` 值指定要放在顶部和底部的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` ，它指定要放大量每一侧的单位数。  
  
 *l*  
 指定要放大量的左侧的单位数 `CRect`。  
  
 *t*  
 指定要放大量顶部的单位数 `CRect`。  
  
 *r*  
 指定要放大量右侧的单位数 `CRect`。  
  
 *b*  
 指定要放大量的底部的单位数 `CRect`。  
  
### <a name="remarks"></a>备注  
 若要这样做， `InflateRect` 减去从 left 和 top 的单元，并将设备添加到右侧和底部。 参数 `InflateRect` 进行了签名值; 正值放大量 `CRect` 和负值 deflate 它。  
  
 前两个重载的放大量的另一侧这两个对 `CRect` ，以便其总宽度增加两倍 *x* (或 `cx`) 和窗体的总高度将增加两倍 *y* (或 `cy`)。 其他两个重载的放大量的每一侧 `CRect` 相互独立地。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#42](../../atl-mfc-shared/codesnippet/CPP/crect-class_8.cpp)]  
  
##  <a name="a-namecrectintersectrecta-crectintersectrect"></a><a name="crect__intersectrect"></a>  CRect::IntersectRect  
 使 `CRect` 等于两个现有矩形的交集。  
  
```  
 
    BOOL IntersectRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `lpRect1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含源矩形。  
  
 `lpRect2`  
 指向 `RECT` 结构或 `CRect` 对象，其中包含源矩形。  
  
### <a name="return-value"></a>返回值  
 如果交集不为空，则为非零值如果交集为空，则为 0。  
  
### <a name="remarks"></a>备注  
 交集是最大的矩形包含在这两个现有矩形中。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#43](../../atl-mfc-shared/codesnippet/CPP/crect-class_9.cpp)]  
  
##  <a name="a-namecrectisrectemptya-crectisrectempty"></a><a name="crect__isrectempty"></a>  CRect::IsRectEmpty  
 确定是否 `CRect` 为空。  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果非零 `CRect` 空; 0 如果 `CRect` 不为空。  
  
### <a name="remarks"></a>备注  
 一个矩形为空如果的宽度和/或高度值为 0 或负数。 不同于 `IsRectNull`, ，从而确定是否所有的矩形的坐标为零。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#44](../../atl-mfc-shared/codesnippet/CPP/crect-class_10.cpp)]  
  
##  <a name="a-namecrectisrectnulla-crectisrectnull"></a><a name="crect__isrectnull"></a>  CRect::IsRectNull  
 确定是否底部上、 左和右值 `CRect` 完全等于 0。  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果非零 `CRect`的顶部，左、 下、 和正确的值是所有等于 0; 否则为 0。  
  
### <a name="remarks"></a>备注  
 不同于 `IsRectEmpty`, ，它确定矩形为空。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#45](../../atl-mfc-shared/codesnippet/CPP/crect-class_11.cpp)]  
  
##  <a name="a-namecrectmovetoxa-crectmovetox"></a><a name="crect__movetox"></a>  CRect::MoveToX  
 调用此函数可将该矩形移到指定的绝对 x 坐标 *x*。  
  
```  
 
void MoveToX(
int   
x) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *x*  
 该矩形的左上角绝对 x 坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#46](../../atl-mfc-shared/codesnippet/CPP/crect-class_12.cpp)]  
  
##  <a name="a-namecrectmovetoxya-crectmovetoxy"></a><a name="crect__movetoxy"></a>  CRect::MoveToXY  
 调用此函数以移动到绝对 x 坐标和 y 坐标指定的矩形。  
  
```  
 
    void MoveToXY(
    int 
    x ,  
    int 
    y) throw();
void MoveToXY(
    POINT 
    point) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *x*  
 该矩形的左上角绝对 x 坐标。  
  
 *y*  
 该矩形的左上角绝对 y 坐标。  
  
 `point`  
 一个 **点** 结构，它指定的矩形的绝对的左上角。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#47](../../atl-mfc-shared/codesnippet/CPP/crect-class_13.cpp)]  
  
##  <a name="a-namecrectmovetoya-crectmovetoy"></a><a name="crect__movetoy"></a>  CRect::MoveToY  
 调用此函数可将该矩形移到指定的绝对 y 轴坐标 *y*。  
  
```  
 
void MoveToY(
int   
y) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *y*  
 该矩形的左上角绝对 y 坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#48](../../atl-mfc-shared/codesnippet/CPP/crect-class_14.cpp)]  
  
##  <a name="a-namecrectnormalizerecta-crectnormalizerect"></a><a name="crect__normalizerect"></a>  Crect:: Normalizerect  
 规范化 `CRect` ，以便为正数，高度和宽度。  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>备注  
 该矩形进行规范化为第四个象限定位，Windows 通常使用的坐标。 `NormalizeRect` 比较的顶部和底部的值，并且如果顶部大于底部交换这二者。 同样，如果左侧大于右侧交换左和右值。 此函数在处理不同的映射模式时很有用，并反转矩形。  
  
> [!NOTE]
>  以下 `CRect` 成员函数需要规范化的矩形才能正常工作︰ [高度](#crect__height), ，[宽度](#crect__width), ，[大小](#crect__size), ，[IsRectEmpty](#crect__isrectempty), ，[PtInRect](#crect__ptinrect), ，[EqualRect](#crect__equalrect), ，[UnionRect](#crect__unionrect), ，[IntersectRect](#crect__intersectrect), ，[SubtractRect](#crect__subtractrect), ，[运算符 = =](#crect__operator__eq_eq), ，[运算符 ！ =](#crect__operator__neq), ，[运算符 &#124;](#crect__operator__or), ，[运算符 &#124; =](#crect__operator__or_eq), ，[运算符 （& a)](#crect__operator__amp_), ，和 [运算符 （& a) =](#crect__operator__amp__eq)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#49](../../atl-mfc-shared/codesnippet/CPP/crect-class_15.cpp)]  
  
##  <a name="a-namecrectoffsetrecta-crectoffsetrect"></a><a name="crect__offsetrect"></a>  CRect::OffsetRect  
 将移动 `CRect` 由指定的偏移量。  
  
```  
 
    void OffsetRect(
    int 
    x ,  
    int 
    y) throw();
void OffsetRect(
    POINT 
    point) throw();
void OffsetRect(
    SIZE 
    size) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要向左移动或向右的量。 它必须是负数，以向左移动。  
  
 *y*  
 指定要上移或下移的量。 它必须是负数，以向上移动。  
  
 `point`  
 包含 [点](../../mfc/reference/point-structure1.md) 结构或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 对象，它指定要移动两个维度。  
  
 `size`  
 包含 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象，它指定要移动两个维度。  
  
### <a name="remarks"></a>备注  
 将移动 `CRect`*x* 沿 x 轴单位并 *y* 沿 y 轴的单位。  *X* 和 *y* 参数是有符号的值，因此 `CRect` 可以向左移动或向右和向上或向下。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#50](../../atl-mfc-shared/codesnippet/CPP/crect-class_16.cpp)]  
  
##  <a name="a-namecrectoperatorlpcrecta-crectoperator-lpcrect"></a><a name="crect__operator_lpcrect"></a>  CRect::operator LPCRECT  
 将转换 `CRect` 到 [LPCRECT](../../mfc/reference/data-types-mfc.md)。  
  
'' 运算符 LPCRECT() const throw （);
```  
  
### Remarks  
 When you use this function, you don't need the address-of ( **&**) operator. This operator will be automatically used when you pass a `CRect` object to a function that expects an **LPCRECT**.  
  
### Example  
 [!code-cpp[NVC_ATLMFC_Utilities#58](../../atl-mfc-shared/codesnippet/CPP/crect-class_17.cpp)]  
  
##  <a name="crect__operator_lprect"></a>  CRect::operator LPRECT  
 Converts a `CRect` to an [LPRECT](../../mfc/reference/data-types-mfc.md).  
  
```  operator LPRECT() throw();
```  
  
### <a name="remarks"></a>备注  
 当使用此函数时，您不需要的地址 ( **&**) 运算符。 在传递时，此运算符将可自动用于 `CRect` 对象传递给需要的函数 `LPRECT`。  
  
### <a name="example"></a>示例  
 请参阅示例 [CRect::operator LPCRECT](#crect__operator_lpcrect)。  
  
##  <a name="a-namecrectoperatoreqa-crectoperator-"></a><a name="crect__operator__eq"></a>  CRect::operator =  
 将分配 *srcRect* 到 `CRect`。  
  
```  
 
void operator=(
const RECT& 
srcRect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 *srcRect*  
 是指源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#59](../../atl-mfc-shared/codesnippet/CPP/crect-class_18.cpp)]  
  
##  <a name="a-namecrectoperatoreqeqa-crectoperator-"></a><a name="crect__operator__eq_eq"></a>  CRect::operator = =  
 确定是否 `rect` 是否等同于 `CRect` 通过比较其左上角和右下角的坐标。  
  
```  
 
BOOL operator==(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 是指源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>返回值  
 非零，如果相等;否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#60](../../atl-mfc-shared/codesnippet/CPP/crect-class_19.cpp)]  
  
##  <a name="a-namecrectoperatorneqa-crectoperator-"></a><a name="crect__operator__neq"></a>  CRect::operator ！ =  
 确定是否 `rect` 是否不等于 `CRect` 通过比较其左上角和右下角的坐标。  
  
```  
 
BOOL operator!=(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 是指源矩形。 可以是 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>返回值  
 如果不等于; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#61](../../atl-mfc-shared/codesnippet/CPP/crect-class_20.cpp)]  
  
##  <a name="a-namecrectoperatoraddeqa-crectoperator-"></a><a name="crect__operator__add_eq"></a>  CRect::operator + =  
 前两个重载移动 `CRect` 由指定的偏移量。  
  
```  
 
void operator+=(
POINT   
point) throw();

void operator+=(
SIZE   
size) throw();

void operator+=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 一个 [点](../../mfc/reference/point-structure1.md) 结构或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 对象，它指定要移动矩形的单位数。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象，它指定要移动矩形的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含要放大量的每一侧的单位数 `CRect`。  
  
### <a name="remarks"></a>备注  
 参数的 *x* 和 *y* (或 `cx` 和 `cy`) 值添加到 `CRect`。  
  
 第三个重载放大 `CRect` 按参数的每个成员中的单元指定数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#62](../../atl-mfc-shared/codesnippet/CPP/crect-class_21.cpp)]  
  
##  <a name="a-namecrectoperator-eqa-crectoperator--"></a><a name="crect__operator_-_eq"></a>  CRect::operator =  
 前两个重载移动 `CRect` 由指定的偏移量。  
  
```  
 
void operator-=(
POINT   
point) throw();

void operator-=(
SIZE   
size) throw();

void operator-=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 一个 [点](../../mfc/reference/point-structure1.md) 结构或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 对象，它指定要移动矩形的单位数。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象，它指定要移动矩形的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含要 deflate 的每一侧的单位数 `CRect`。  
  
### <a name="remarks"></a>备注  
 参数的 *x* 和 *y* (或 `cx` 和 `cy`) 值相减从 `CRect`。  
  
 第三个重载压缩 `CRect` 按参数的每个成员中的单元指定数。 请注意，此重载方法的功能类似 [DeflateRect](#crect__deflaterect)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#63](../../atl-mfc-shared/codesnippet/CPP/crect-class_22.cpp)]  
  
##  <a name="a-namecrectoperatorampeqa-crectoperator-amp"></a><a name="crect__operator__amp__eq"></a>  CRect::operator &amp;=  
 集 `CRect` 相等的交集 `CRect` 和 `rect`。  
  
```  
 
void operator&=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="remarks"></a>备注  
 交集是最大的矩形包含在两个矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 请参阅示例 [CRect::IntersectRect](#crect__intersectrect)。  
  
##  <a name="a-namecrectoperatororeqa-crectoperator-124"></a><a name="crect__operator__or_eq"></a>  CRect::operator &#124; =  
 集 `CRect` 等于的并集 `CRect` 和 `rect`。  
  
```  
 
void operator|=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 包含 `CRect` 或 [RECT](../../mfc/reference/rect-structure1.md)。  
  
### <a name="remarks"></a>备注  
 联合是包含两个源矩形的最小矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#64](../../atl-mfc-shared/codesnippet/CPP/crect-class_23.cpp)]  
  
##  <a name="a-namecrectoperatoradda-crectoperator-"></a><a name="crect__operator__add"></a>  CRect::operator +  
 前两个重载均返回 `CRect` 对象，它等于 `CRect` 移置开指定的偏移量。  
  
```  
 
CRect operator+(
POINT   
point) const throw();

CRect operator+(
LPCRECT   
lpRect) const throw();

CRect operator+(
SIZE   
size) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 一个 [点](../../mfc/reference/point-structure1.md) 结构或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 对象，它指定要移动的返回值的单位数。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构或 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象，它指定要移动的返回值的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含要返回的值的每一侧的放大量的单位数。  
  
### <a name="return-value"></a>返回值  
  `CRect` 所得移动或升高了 `CRect` 的参数中指定的单位数。  
  
### <a name="remarks"></a>备注  
 参数的 *x* 和 *y* (或 `cx` 和 `cy`) 参数添加到 `CRect`的位置。  
  
 第三个重载返回一个新 `CRect` ，它等于 `CRect` 急剧增加的每个成员的参数中的单元指定数目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#65](../../atl-mfc-shared/codesnippet/CPP/crect-class_24.cpp)]  
  
##  <a name="a-namecrectoperator-a-crectoperator--"></a><a name="crect__operator_-"></a>  CRect::operator-  
 前两个重载均返回 `CRect` 对象，它等于 `CRect` 移置开指定的偏移量。  
  
```  
 
CRect operator-(
POINT   
point) const throw();

CRect operator-(
SIZE   
size) const throw();

CRect operator-(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 一个 [点](../../mfc/reference/point-structure1.md) 结构或 `CPoint` 对象，它指定要移动的返回值的单位数。  
  
 `size`  
 一个 [大小](http://msdn.microsoft.com/library/windows/desktop/dd145106) 结构或 `CSize` 对象，它指定要移动的返回值的单位数。  
  
 `lpRect`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象，其中包含要 deflate 的返回值的每一侧的单位数。  
  
### <a name="return-value"></a>返回值  
  `CRect` 所得移动或以放气 `CRect` 的参数中指定的单位数。  
  
### <a name="remarks"></a>备注  
 参数的 *x* 和 *y* (或 `cx` 和 `cy`) 参数从中减去 `CRect`的位置。  
  
 第三个重载返回一个新 `CRect` ，它等于 `CRect` 伸缩单位指定参数的每个成员中的数。 请注意，此重载方法的功能类似 [DeflateRect](#crect__deflaterect), ，而不 [SubtractRect](#crect__subtractrect)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#66](../../atl-mfc-shared/codesnippet/CPP/crect-class_25.cpp)]  
  
##  <a name="a-namecrectoperatorampa-crectoperator-amp"></a><a name="crect__operator__amp_"></a>  CRect::operator &amp;  
 返回 `CRect` 即的交集 `CRect` 和 *rect2*。  
  
```  
 
CRect operator&(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 *rect2*  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>返回值  
 一个 `CRect` 即的交集 `CRect` 和 *rect2*。  
  
### <a name="remarks"></a>备注  
 交集是最大的矩形包含在两个矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#67](../../atl-mfc-shared/codesnippet/CPP/crect-class_26.cpp)]  
  
##  <a name="a-namecrectoperatorora-crectoperator-124"></a><a name="crect__operator__or"></a>  CRect::operator &#124;  
 返回 `CRect` 即的并集 `CRect` 和 *rect2*。  
  
```  
 
CRect operator|(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 *rect2*  
 包含 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect`。  
  
### <a name="return-value"></a>返回值  
 一个 `CRect` 即的并集 `CRect` 和 *rect2*。  
  
### <a name="remarks"></a>备注  
 联合是包含两个矩形的最小矩形。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#68](../../atl-mfc-shared/codesnippet/CPP/crect-class_27.cpp)]  
  
##  <a name="a-namecrectptinrecta-crectptinrect"></a><a name="crect__ptinrect"></a>  CRect::PtInRect  
 确定指定的点是否位于内 `CRect`。  
  
```  
 
BOOL PtInRect(
POINT   
point) const throw();

 
```  
  
### <a name="parameters"></a>参数  
 `point`  
 包含 [点](../../mfc/reference/point-structure1.md) 结构或 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 对象。  
  
### <a name="return-value"></a>返回值  
 如果该点位于内，则为非 `CRect`; 否则为 0。  
  
### <a name="remarks"></a>备注  
 点内，则 `CRect` 如果它位于上的向左或前一侧或在所有四个边。 点的右侧或底部的一端位于外部 `CRect`。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#51](../../atl-mfc-shared/codesnippet/CPP/crect-class_28.cpp)]  
  
##  <a name="a-namecrectsetrecta-crectsetrect"></a><a name="crect__setrect"></a>  CRect::SetRect  
 设置的尺寸 `CRect` 为指定的坐标。  
  
```  
 
    void SetRect(
    int 
    x1 ,  
    int 
    y1 ,  
    int 
    x2 ,  
    int 
    y2) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定窗口左上角的 x 坐标。  
  
 `y1`  
 指定窗口左上角的 y 坐标。  
  
 `x2`  
 指定的右下角的 x 坐标。  
  
 `y2`  
 指定的右下角的 y 坐标。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#52](../../atl-mfc-shared/codesnippet/CPP/crect-class_29.cpp)]  
  
##  <a name="a-namecrectsetrectemptya-crectsetrectempty"></a><a name="crect__setrectempty"></a>  CRect::SetRectEmpty  
 使 `CRect` 通过将所有坐标都设置为零的空矩形。  
  
```  
void SetRectEmpty() throw();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#53](../../atl-mfc-shared/codesnippet/CPP/crect-class_30.cpp)]  
  
##  <a name="a-namecrectsizea-crectsize"></a><a name="crect__size"></a>  CRect::Size  
  `cx` 和 `cy` 成员的返回值包含高度和宽度 `CRect`。  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>返回值  
 一个 [CSize](../../atl-mfc-shared/reference/csize-class.md) 对象，其中包含的大小 `CRect`。  
  
### <a name="remarks"></a>备注  
 高度或宽度可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#54](../../atl-mfc-shared/codesnippet/CPP/crect-class_31.cpp)]  
  
##  <a name="a-namecrectsubtractrecta-crectsubtractrect"></a><a name="crect__subtractrect"></a>  CRect::SubtractRect  
 使的尺寸 **CRect** 等于减去 `lpRectSrc2` 从 `lpRectSrc1`。  
  
```  
 
    BOOL SubtractRect(
    LPCRECT 
    lpRectSrc1 ,  
    LPCRECT 
    lpRectSrc2) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `lpRectSrc1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 结构或 `CRect` 对象是要减去一个矩形。  
  
 `lpRectSrc2`  
 指向 `RECT` 结构或 `CRect` 指向对象，它是被减数矩形 `lpRectSrc1` 参数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 减法运算是包含所有的点的最小矩形 `lpRectScr1` 的交集中的不是 `lpRectScr1` 和 *lpRectScr2*。  
  
 指定的矩形 `lpRectSrc1` 将保持不变，如果指定的矩形 `lpRectSrc2` 不与指定的矩形完全重叠 *lpRectSrc1* 中至少一个的 x 或 y 的方向。  
  
 例如，如果 `lpRectSrc1` 已 10,10 (100100） 和 `lpRectSrc2` 已 50,50 (150,150），指向该矩形 `lpRectSrc1` 函数返回时将保持不变。 如果 `lpRectSrc1` 已 10,10 (100100） 和 `lpRectSrc2` 已 50,10 (150,150），但是，该矩形指向 `lpRectSrc1` 将包含的坐标 （10,10、 50100） 时返回该函数。  
  
 `SubtractRect` 不是与相同 [运算符-](#crect__operator_-) ，也不 [运算符-=](#crect__operator_-_eq)。 这些运算符任一曾经调用 `SubtractRect`。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#55](../../atl-mfc-shared/codesnippet/CPP/crect-class_32.cpp)]  
  
##  <a name="a-namecrecttoplefta-crecttopleft"></a><a name="crect__topleft"></a>  CRect::TopLeft  
 作为引用返回坐标 [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) 中包含的对象 `CRect`。  
  
```  
 
CPoint& TopLeft() throw();

const CPoint& TopLeft() const throw();

 
```  
  
### <a name="return-value"></a>返回值  
 矩形的左上角的坐标。  
  
### <a name="remarks"></a>备注  
 此函数可用于获取或设置的矩形的左上角。 设置通过使用此函数在赋值运算符的左侧角。  
  
### <a name="example"></a>示例  
 请参阅示例 [CRect::CenterPoint](#crect__centerpoint)。  
  
##  <a name="a-namecrectunionrecta-crectunionrect"></a><a name="crect__unionrect"></a>  CRect::UnionRect  
 使的尺寸 `CRect` 等于两个源矩形的并集。  
  
```  
 
    BOOL UnionRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>参数  
 `lpRect1`  
 指向 [RECT](../../mfc/reference/rect-structure1.md) 或 `CRect` ，其中包含源矩形。  
  
 `lpRect2`  
 指向 `RECT` 或 `CRect` ，其中包含源矩形。  
  
### <a name="return-value"></a>返回值  
 如果联合不为空，则为非零值如果是空的并集，则为 0。  
  
### <a name="remarks"></a>备注  
 联合是包含两个源矩形的最小矩形。  
  
 Windows 将忽略为空矩形; 的维度它是一个矩形，它不具有任何高度或具有没有宽度。  
  
> [!NOTE]
>  这两个矩形必须规范化或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#56](../../atl-mfc-shared/codesnippet/CPP/crect-class_33.cpp)]  
  
##  <a name="a-namecrectwidtha-crectwidth"></a><a name="crect__width"></a>  CRect::Width  
 计算的宽度 `CRect` 通过减去右值的左的值。  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>返回值  
 宽度 `CRect`。  
  
### <a name="remarks"></a>备注  
 宽度可以是负值。  
  
> [!NOTE]
>  必须规范化矩形或此函数可能会失败。 您可以调用 [NormalizeRect](#crect__normalizerect) 来调用此函数之前规范化该矩形。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#57](../../atl-mfc-shared/codesnippet/CPP/crect-class_34.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPoint 类](../../atl-mfc-shared/reference/cpoint-class.md)   
 [CSize 类](../../atl-mfc-shared/reference/csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)

