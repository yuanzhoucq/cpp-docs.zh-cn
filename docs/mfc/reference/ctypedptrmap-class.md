---
title: "CTypedPtrMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections
- template classes, CTypedPtrMap class
- maps
- CTypedPtrMap class
- pointer maps
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 919d751c6ffe4b10ffad047f1b6be832bf49a1af
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap Class
为 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`指针映射类的对象提供安全类型“包装器”。  
  
## <a name="syntax"></a>语法  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 类型化的指针映射类; 基类必须为指针映射类 ( `CMapPtrToPtr`， `CMapPtrToWord`， `CMapWordToPtr`，或`CMapStringToPtr`)。  
  
 `KEY`  
 用作到映射的键的对象类。  
  
 `VALUE`  
 存储在映射中的对象的类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|  
|[CTypedPtrMap::Lookup](#lookup)|返回`KEY`基于`VALUE`。|  
|[CTypedPtrMap::RemoveKey](#removekey)|移除由键指定的元素。|  
|[CTypedPtrMap::SetAt](#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CTypedPtrMap::operator]](#operator_at)|将元素插入到映射。|  
  
## <a name="remarks"></a>备注  
 当您使用`CTypedPtrMap`，c + + 类型检查功能可帮助消除错误引起的不匹配的指针类型。  
  
 因为所有`CTypedPtrMap`函数将以内联方式，使用此模板不会严重影响的大小或代码的速度。  
  
 有关详细信息使用`CTypedPtrMap`，请参阅文章[集合](../../mfc/collections.md)和[基于模板的类](../../mfc/template-based-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 检索处的地图元素`rNextPosition`，然后更新`rNextPosition`来指代映射中的下一个元素。  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 指定对引用**位置**返回先前值`GetNextAssoc`或`BASE_CLASS` **:: GetStartPosition**调用。  
  
 *密钥*  
 指定地图的键的类型的模板参数。  
  
 `rKey`  
 指定的检索的元素返回的键。  
  
 *值*  
 指定的映射值的类型的模板参数。  
  
 `rValue`  
 指定检索的元素的返回的值。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于循环访问映射中的所有元素。 请注意，位置序列并不一定为键值序列相同。  
  
 如果检索的元素则在映射中，最后的新值`rNextPosition`设置为**NULL**。  
  
 此内联函数将调用`BASE_CLASS` **:: GetNextAssoc**。  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`使用哈希算法来快速找到完全匹配的密钥的地图元素。  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `BASE_CLASS`  
 指定此地图的类的基类的模板参数。  
  
 `key`  
 要查找的元素的键。  
  
 *值*  
 指定此地图中的存储值的类型的模板参数。  
  
 `rValue`  
 指定检索的元素的返回的值。  
  
### <a name="return-value"></a>返回值  
 如果该元素; 如果未找到，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此内联函数将调用`BASE_CLASS` **:: 查找**。  
  
##  <a name="operator_at"></a>CTypedPtrMap::operator]  
 仅在赋值语句 （左值） 的左侧，可以使用此运算符。  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>参数  
 *值*  
 指定此地图中的存储值的类型的模板参数。  
  
 `BASE_CLASS`  
 指定此地图的类的基类的模板参数。  
  
 `key`  
 要查找或创建在映射中的元素的键。  
  
### <a name="remarks"></a>备注  
 如果没有地图元素与指定的键，则创建一个新的元素。 等效于此运算符的没有"右侧"（右值），因为一个密钥可能无法找到在映射中的可能性。 使用`Lookup`元素检索的成员函数。  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 此成员函数将调用`BASE_CLASS` **:: RemoveKey**。  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>参数  
 *密钥*  
 指定地图的键的类型的模板参数。  
  
 `key`  
 要移除的元素键。  
  
### <a name="return-value"></a>返回值  
 如果找到并成功移除，则将该条目，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 有关更详细的备注，请参阅[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)。  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 此成员函数将调用`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>参数  
 *密钥*  
 指定地图的键的类型的模板参数。  
  
 `key`  
 指定 newValue 的键值。  
  
 `newValue`  
 指定是将新元素的值的对象指针。  
  
### <a name="remarks"></a>备注  
 有关更详细的备注，请参阅[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr 类](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)

