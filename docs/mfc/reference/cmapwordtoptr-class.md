---
title: "CMapWordToPtr 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapWordToPtr
dev_langs:
- C++
helpviewer_keywords:
- 16-bit word mapping
- CMapWordToPtr class
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
caps.latest.revision: 22
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 982d42b1204d57e2abf76498b90c17864db34fb9
ms.lasthandoff: 02/24/2017

---
# <a name="cmapwordtoptr-class"></a>CMapWordToPtr 类
支持 16 位键控的 void 指针的映射。  
  
## <a name="syntax"></a>语法  
  
```  
class CMapWordToPtr : public CObject  
```  
  
## <a name="members"></a>成员  
 成员函数`CMapWordToPtr`类似于类的成员函数[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论您在何处找到作为函数参数的 `CObject` 或返回值，都将替换指向 `void` 的指针。 无论您在何处`CString`或**const**指针，指向`char`作为函数参数或返回值，替换**WORD**。  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 例如，转换为  
  
 `BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|此映射中返回元素的数。|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定当前的哈希表中的元素数。|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取用于循环的下一个元素。|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|此映射中返回元素的数。|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回的第一个元素的位置。|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定的键的哈希值。|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|测试空映射条件 （元素）。|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查找基于 void 指针键的 void 指针。 指针值，而不是它指向的实体用于键的比较。|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回与指定的键值关联的键的引用。|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此映射中移除所有元素。|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射 — 的运算符替换`SetAt`。|  
  
## <a name="remarks"></a>备注  
 `CMapWordToPtr` 合并 `IMPLEMENT_DYNAMIC` 宏来支持运行时类型访问和转储到 `CDumpContext` 对象。 如果您需要单独的地图元素的转储，必须将转储上下文的深度设置为 1 或更高。  
  
 Word 指针映射可能不会序列化。  
  
 当`CMapWordToPtr`对象被删除，或当移除其元素，删除的单词，并且指针。 不会删除由指针引用的实体。  
  
 有关详细信息`CMapWordToPtr`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToPtr`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcoll.h  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




