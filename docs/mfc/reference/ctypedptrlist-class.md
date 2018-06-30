---
title: CTypedPtrList 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3f74782241ec69d77ec55b8613c59f87adb40fb
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122825"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 类
为 `CPtrList`类的对象提供安全类型“包装器”。  
  
## <a name="syntax"></a>语法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>参数  
 *BASE_CLASS*  
 类的基类类型化的指针列表;必须是一个指针的列表类 (`CObList`或`CPtrList`)。  
  
 *类型*  
 基类列表中存储的元素的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （使新头） 的列表的开头。|  
|[CTypedPtrList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到列表 （使新尾） 生成后半部分。|  
|[CTypedPtrList::GetAt](#getat)|获取位于给定位置的元素。|  
|[CTypedPtrList::GetHead](#gethead)|返回的列表中 （不能为空） 的头元素。|  
|[CTypedPtrList::GetNext](#getnext)|获取循环的下一个元素。|  
|[CTypedPtrList::GetPrev](#getprev)|获取循环访问的上一个元素。|  
|[CTypedPtrList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|  
|[CTypedPtrList::RemoveHead](#removehead)|从列表头与列表中移除的元素。|  
|[CTypedPtrList::RemoveTail](#removetail)|从列表的结尾移除的元素。|  
|[CTypedPtrList::SetAt](#setat)|设置给定位置处的元素。|  
  
## <a name="remarks"></a>备注  
 当你使用`CTypedPtrList`而非`CObList`或`CPtrList`，c + + 类型检查工具可帮助消除错误引起的不匹配的指针类型。  
  
 此外，`CTypedPtrList`包装执行大量如果你使用所需的强制转换`CObList`或`CPtrList`。  
  
 因为所有`CTypedPtrList`函数内联，使用此模板不会显著影响大小或代码的速度。  
  
 列表派生自`CObList`可序列化，但派生自`CPtrList`不能。  
  
 当删除 `CTypedPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。  
  
 有关详细信息使用`CTypedPtrList`，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。  
  
## <a name="example"></a>示例  
 此示例中创建的实例`CTypedPtrList`将添加一个对象，序列化到磁盘，列表，然后删除该对象：  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="addhead"></a>  CTypedPtrList::AddHead  
 此成员函数将调用`BASE_CLASS` **:: AddHead**。  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 基类列表中存储的元素的类型。  
  
 *newElement*  
 要添加到此列表的对象指针。 允许 NULL 值。  
  
 *BASE_CLASS*  
 类的基类类型化的指针列表;必须是一个指针的列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 *pNewList*  
 指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素*pNewList*将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回新插入的元素的位置值。  
  
### <a name="remarks"></a>备注  
 第一个版本中添加新元素列表的开头之前。 第二个版本将添加前头元素的另一个的列表。  
  
##  <a name="addtail"></a>  CTypedPtrList::AddTail  
 此成员函数将调用`BASE_CLASS` **:: AddTail**。  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 基类列表中存储的元素的类型。  
  
 *newElement*  
 要添加到此列表的对象指针。 允许 NULL 值。  
  
 *BASE_CLASS*  
 类的基类类型化的指针列表;必须是一个指针的列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 *pNewList*  
 指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素*pNewList*将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回新插入的元素的位置值。  
  
### <a name="remarks"></a>备注  
 第一个版本之后列表末尾添加一个新的元素。 第二个版本将元素的另一个列表添加列表的结尾之后。  
  
##  <a name="getat"></a>  CTypedPtrList::GetAt  
 类型位置的变量的至关重要的列表。  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在列表中元素的类型。  
  
 *位置*  
 先前的返回位置值`GetHeadPosition`或`Find`成员函数调用。  
  
### <a name="return-value"></a>返回值  
 如果通过指针访问列表`const CTypedPtrList`，然后`GetAt`返回由模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此进行修改，保护列表。  
  
 如果直接或通过指针访问列表`CTypedPtrList`，然后`GetAt`返回对指定模板参数的类型的指针的引用*类型*。 这允许要在赋值语句的任何一侧上使用的函数，从而允许对要修改的列表项。  
  
### <a name="remarks"></a>备注  
 它并不相同索引，并且你无法对值进行运算位置自己。 `GetAt` 检索`CObject`给定位置与关联的指针。  
  
 你必须确保你的位置值表示在列表中的有效位置。 如果它是无效的 Microsoft 基础类库的调试版本断言。  
  
 此内联函数调用`BASE_CLASS` **:: GetAt**。  
  
##  <a name="gethead"></a>  CTypedPtrList::GetHead  
 获取表示此列表的头元素的指针。  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在列表中元素的类型。  
  
### <a name="return-value"></a>返回值  
 如果通过指针访问列表`const CTypedPtrList`，然后`GetHead`返回由模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此进行修改，保护列表。  
  
 如果直接或通过指针访问列表`CTypedPtrList`，然后`GetHead`返回对指定模板参数的类型的指针的引用*类型*。 这允许要在赋值语句的任何一侧上使用的函数，从而允许对要修改的列表项。  
  
### <a name="remarks"></a>备注  
 你必须确保该列表不是空之前调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表包含的元素。  
  
##  <a name="getnext"></a>  CTypedPtrList::GetNext  
 获取标识的列表元素*rPosition*，然后设置*rPosition*到列表中的下一步条目的位置值。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定此列表中包含的元素的类型的模板参数。  
  
 *rPosition*  
 对先前返回的位置值的引用`GetNext`， `GetHeadPosition`，或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 如果通过指针访问列表`const CTypedPtrList`，然后`GetNext`返回由模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此进行修改，保护列表。  
  
 如果直接或通过指针访问列表`CTypedPtrList`，然后`GetNext`返回对指定模板参数的类型的指针的引用*类型*。 这允许要在赋值语句的任何一侧上使用的函数，从而允许对要修改的列表项。  
  
### <a name="remarks"></a>备注  
 你可以使用`GetNext`如果建立通过调用的初始位置的向前迭代循环中`GetHeadPosition`或[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。  
  
 你必须确保你的位置值表示在列表中的有效位置。 如果它是无效的 Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素的是在列表中，最后然后的新值*rPosition*设置为 NULL。  
  
 可迭代过程中删除元素。 请参阅示例[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。  
  
##  <a name="getprev"></a>  CTypedPtrList::GetPrev  
 获取标识的列表元素*rPosition*，然后设置*rPosition*到列表的上一项的位置值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定此列表中包含的元素的类型的模板参数。  
  
 *rPosition*  
 对先前返回的位置值的引用`GetPrev`或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 如果通过指针访问列表`const CTypedPtrList`，然后`GetPrev`返回由模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此进行修改，保护列表。  
  
 如果直接或通过指针访问列表`CTypedPtrList`，然后`GetPrev`返回对指定模板参数的类型的指针的引用*类型*。 这允许要在赋值语句的任何一侧上使用的函数，从而允许对要修改的列表项。  
  
### <a name="remarks"></a>备注  
 你可以使用`GetPrev`如果建立通过调用的初始位置的反向迭代循环中`GetTailPosition`或`Find`。  
  
 你必须确保你的位置值表示在列表中的有效位置。 如果它是无效的 Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素的是在列表中，第一个然后的新值*rPosition*设置为 NULL。  
  
##  <a name="gettail"></a>  CTypedPtrList::GetTail  
 获取表示此列表的头元素的指针。  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在列表中元素的类型。  
  
### <a name="return-value"></a>返回值  
 如果通过指针访问列表`const CTypedPtrList`，然后`GetTail`返回由模板参数指定的类型的指针*类型*。 这允许使用仅在赋值语句右侧的函数，因此进行修改，保护列表。  
  
 如果直接或通过指针访问列表`CTypedPtrList`，然后`GetTail`返回对指定模板参数的类型的指针的引用*类型*。 这允许要在赋值语句的任何一侧上使用的函数，从而允许对要修改的列表项。  
  
### <a name="remarks"></a>备注  
 你必须确保该列表不是空之前调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表包含的元素。  
  
##  <a name="removehead"></a>  CTypedPtrList::RemoveHead  
 从列表头与列表中移除的元素，并将其返回。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在列表中元素的类型。  
  
### <a name="return-value"></a>返回值  
 以前位于最前面的列表的指针。 此指针为由模板参数指定的类型*类型*。  
  
### <a name="remarks"></a>备注  
 你必须确保该列表不是空之前调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表包含的元素。  
  
##  <a name="removetail"></a>  CTypedPtrList::RemoveTail  
 从列表的结尾移除的元素，并将其返回。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数来指定存储在列表中元素的类型。  
  
### <a name="return-value"></a>返回值  
 以前处列表末尾的指针。 此指针为由模板参数指定的类型*类型*。  
  
### <a name="remarks"></a>备注  
 你必须确保该列表不是空之前调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表包含的元素。  
  
##  <a name="setat"></a>  CTypedPtrList::SetAt  
 此成员函数将调用`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 *pos*  
 要设置的元素的位置。  
  
 *类型*  
 基类列表中存储的元素的类型。  
  
 *newElement*  
 要写入到列表的对象指针。  
  
### <a name="remarks"></a>备注  
 类型位置的变量的至关重要的列表。 它并不相同索引，并且你无法对值进行运算位置自己。 `SetAt` 将写入列表中的指定位置的对象指针。  
  
 你必须确保你的位置值表示在列表中的有效位置。 如果它是无效的 Microsoft 基础类库的调试版本断言。  
  
 有关详细说明，请参阅[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPtrList 类](../../mfc/reference/cptrlist-class.md)   
 [CObList 类](../../mfc/reference/coblist-class.md)
