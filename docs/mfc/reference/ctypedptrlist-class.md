---
title: "CTypedPtrList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrList
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList class
- type-safe collections
- lists [C++]
- template classes, CTypedPtrList class
- linked lists [C++]
- pointer lists
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: 24
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
ms.openlocfilehash: ca8d868333aa977710e387fc1bb13271dc8f99fa
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 类
为 `CPtrList`类的对象提供安全类型“包装器”。  
  
## <a name="syntax"></a>语法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 类的基类类型化的指针列表;必须是一个指针的列表类 (`CObList`或`CPtrList`)。  
  
 `TYPE`  
 存储在基类列表中的元素的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的头） 的列表的开头。|  
|[CTypedPtrList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的结尾） 列表的末尾。|  
|[CTypedPtrList::GetAt](#getat)|获取位于给定位置的元素。|  
|[CTypedPtrList::GetHead](#gethead)|返回的列表 （不能为空） 的头元素。|  
|[CTypedPtrList::GetNext](#getnext)|获取用于循环的下一个元素。|  
|[CTypedPtrList::GetPrev](#getprev)|获取循环访问的上一个元素。|  
|[CTypedPtrList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|  
|[CTypedPtrList::RemoveHead](#removehead)|从列表头中移除的元素。|  
|[CTypedPtrList::RemoveTail](#removetail)|从列表的结尾移除的元素。|  
|[CTypedPtrList::SetAt](#setat)|设置给定位置的元素。|  
  
## <a name="remarks"></a>备注  
 当您使用`CTypedPtrList`而不是`CObList`或`CPtrList`，c + + 类型检查功能可帮助消除错误引起的不匹配的指针类型。  
  
 此外，`CTypedPtrList`包装执行大量的强制转换，如果您使用了所需`CObList`或`CPtrList`。  
  
 因为所有`CTypedPtrList`函数将以内联方式，使用此模板不会严重影响的大小或代码的速度。  
  
 列表派生自`CObList`可序列化，但那些从派生`CPtrList`不能。  
  
 当删除 `CTypedPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。  
  
 有关详细信息使用`CTypedPtrList`，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。  
  
## <a name="example"></a>示例  
 此示例中创建的一个实例`CTypedPtrList`、 添加一个对象、 序列化到磁盘上，列表，然后删除该对象︰  
  
 [!code-cpp[NVC_MFCCollections #&110;](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #&111;](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="a-nameaddheada--ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::AddHead  
 此成员函数将调用`BASE_CLASS` **:: AddHead**。  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 存储在基类列表中的元素的类型。  
  
 `newElement`  
 要添加到此列表的对象指针。 一个**NULL**允许值。  
  
 `BASE_CLASS`  
 类的基类类型化的指针列表;必须是一个指针的列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 `pNewList`  
 一个指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
### <a name="remarks"></a>备注  
 第一个版本中添加新元素前对列表头。 第二个版本将添加另一个列表前头元素。  
  
##  <a name="a-nameaddtaila--ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail  
 此成员函数将调用`BASE_CLASS` **:: AddTail**。  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 存储在基类列表中的元素的类型。  
  
 `newElement`  
 要添加到此列表的对象指针。 一个**NULL**允许值。  
  
 `BASE_CLASS`  
 类的基类类型化的指针列表;必须是一个指针的列表类 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 `pNewList`  
 一个指向另一个[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)对象。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
### <a name="remarks"></a>备注  
 第一个版本后列表末尾添加新元素。 第二个版本在列表的结尾之后添加另一个元素的列表。  
  
##  <a name="a-namegetata--ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt  
 类型的变量**位置**至关重要的列表。  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定存储在列表中的元素类型的模板参数。  
  
 *位置*  
 一个**位置**返回先前值`GetHeadPosition`或**查找**成员函数调用。  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CTypedPtrList**，然后`GetAt`返回指定模板参数的类型的指针*类型*。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetAt`返回对指定的模板参数的类型的指针的引用*类型*。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 `GetAt`检索`CObject`与给定位置相关联的指针。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 此内联函数将调用`BASE_CLASS` **:: GetAt**。  
  
##  <a name="a-namegetheada--ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead  
 获取表示此列表的头元素的指针。  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定存储在列表中的元素类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CTypedPtrList**，然后`GetHead`返回指定模板参数的类型的指针*类型*。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetHead`返回对指定的模板参数的类型的指针的引用*类型*。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。  
  
##  <a name="a-namegetnexta--ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到**位置**列表中的下一个条目的值。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定此列表中包含的元素的类型的模板参数。  
  
 `rPosition`  
 对引用**位置**返回先前值`GetNext`， `GetHeadPosition`，或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CTypedPtrList**，然后`GetNext`返回指定模板参数的类型的指针*类型*。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetNext`返回对指定的模板参数的类型的指针的引用*类型*。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetNext`在向前迭代循环中，如果您建立的初始位置，通过调用`GetHeadPosition`或[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，最后的新值`rPosition`设置为**NULL**。  
  
 可执行迭代的过程中删除元素。 请参阅示例[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。  
  
##  <a name="a-namegetpreva--ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到**位置**以前在列表中项的值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定此列表中包含的元素的类型的模板参数。  
  
 `rPosition`  
 对引用**位置**返回先前值`GetPrev`或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CTypedPtrList**，然后`GetPrev`返回指定模板参数的类型的指针*类型*。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetPrev`返回对指定的模板参数的类型的指针的引用*类型*。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetPrev`在反向迭代循环中，如果您建立的初始位置，通过调用`GetTailPosition`或**查找**。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，第一个的新值`rPosition`设置为**NULL**。  
  
##  <a name="a-namegettaila--ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail  
 获取表示此列表的头元素的指针。  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定存储在列表中的元素类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CTypedPtrList**，然后`GetTail`返回指定模板参数的类型的指针*类型*。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CTypedPtrList`，然后`GetTail`返回对指定的模板参数的类型的指针的引用*类型*。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。  
  
##  <a name="a-nameremoveheada--ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead  
 从列表头中移除的元素并将其返回。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定存储在列表中的元素类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 以前在列表头的指针。 此指针为指定的模板参数的类型*类型*。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。  
  
##  <a name="a-nameremovetaila--ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail  
 从列表的结尾移除的元素并将其返回。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定存储在列表中的元素类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 以前处列表末尾的指针。 此指针为指定的模板参数的类型*类型*。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。  
  
##  <a name="a-namesetata--ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt  
 此成员函数将调用`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 **位置**要设置的元素。  
  
 *类型*  
 存储在基类列表中的元素的类型。  
  
 `newElement`  
 要写入到列表的对象指针。  
  
### <a name="remarks"></a>备注  
 类型的变量**位置**至关重要的列表。 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 `SetAt`在列表中的指定位置中写入的对象指针。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 有关更详细的备注，请参阅[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPtrList 类](../../mfc/reference/cptrlist-class.md)   
 [CObList 类](../../mfc/reference/coblist-class.md)

