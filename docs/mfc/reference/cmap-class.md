---
title: "CMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- dictionary mapping class
- collection classes, dictionary mapping
- CMap class
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
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
ms.openlocfilehash: 680d44fe6154861d2c638697cfc9d3fbeab36cc4
ms.lasthandoff: 02/24/2017

---
# <a name="cmap-class"></a>CMap 类
将唯一键映射到值的字典集合类。  
  
## <a name="syntax"></a>语法  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>参数  
 `KEY`  
 用作到映射的键的对象类。  
  
 `ARG` *_* `KEY`  
 数据类型用于`KEY`参数; 通常指`KEY`。  
  
 `VALUE`  
 存储在映射中的对象的类。  
  
 `ARG` *_* `VALUE`  
 数据类型用于`VALUE`参数; 通常指`VALUE`。  
  
## <a name="members"></a>成员  
  
### <a name="public-structures"></a>公共结构  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|一个包含密钥的值和关联的对象的值的嵌套的结构。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|构造了键映射到值的集合。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|此映射中返回元素的数。|  
|[CMap::GetHashTableSize](#gethashtablesize)|返回哈希表中的元素数。|  
|[CMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|  
|[CMap::GetSize](#getsize)|此映射中返回元素的数。|  
|[CMap::GetStartPosition](#getstartposition)|返回的第一个元素的位置。|  
|[CMap::InitHashTable](#inithashtable)|初始化哈希表，并指定其大小。|  
|[CMap::IsEmpty](#isempty)|测试空映射条件 （元素）。|  
|[CMap::Lookup](#lookup)|查找映射到给定键的值。|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|返回指向第一个元素的指针。|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|获取一个指向下一个元素的循环。|  
|[CMap::PLookup](#plookup)|返回一个指向其值与指定的值匹配的键。|  
|[CMap::RemoveAll](#removeall)|此映射中移除所有元素。|  
|[CMap::RemoveKey](#removekey)|移除由键指定的元素。|  
|[CMap::SetAt](#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CMap::operator]](#operator_at)|将元素插入到映射 â €"的运算符替换`SetAt`。|  
  
## <a name="remarks"></a>备注  
 一旦已插入到映射的键 / 值对 （元素），您可以高效地检索或删除使用该密钥来访问它的对。 此外可以循环访问映射中的所有元素。  
  
 类型的变量**位置**用于备用项的访问。 您可以使用**位置**"记住"条目并循环访问该映射。 您可能会认为，此小版本是顺序由键值;不是这样。 检索元素的顺序是不确定的。  
  
 此类调用全局帮助器函数的某些成员函数必须进行自定义的大部分使用`CMap`类。 请参阅[集合类帮助器](../../mfc/reference/collection-class-helpers.md)中的宏和全局函数部分`MFC``Reference`。  
  
 `CMap`重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)用于支持序列化和转储的它的元素。 如果映射存储到存档使用`Serialize`，每个地图元素将依次序列化。 默认实现`SerializeElements`helper 函数执行的位写入。 有关指针集合项的序列化信息派生自`CObject`或其他用户定义类型，请参阅[如何︰ 创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果您需要在映射 （键和值） 中的各个元素的诊断转储，您必须设置为 1 或更高版本的转储上下文的深度。  
  
 当`CMap`对象被删除，或当移除其元素，删除密钥和值。  
  
 映射类的派生是类似于列表派生。 请参阅文章[集合](../../mfc/collections.md)举例说明了一个专用的列表类派生的。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="cmap"></a>CMap::CMap  
 构造一个空的映射。  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 指定扩展映射的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 随着该映射的增长，单位为分配内存`nBlockSize`条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&56;](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 包含一个键值和关联的对象的值。  
  
### <a name="remarks"></a>备注  
 这是在类中的嵌套的结构[CMap](../../mfc/reference/cmap-class.md)。  
  
 该结构由两个字段组成︰  
  
- **keyÂ Â Â**密钥类型的实际值。  
  
- **价值 Â Â**关联对象的值。  
  
 它用于存储的返回值[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，和[CMap::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>示例  
 有关用法的示例，请参阅示例[CMap::PLookup](#plookup)。  
  
##  <a name="getcount"></a>CMap::GetCount  
 检索映射中的元素的数目。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 元素数量。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::Lookup](#lookup)。  
  
##  <a name="gethashtablesize"></a>CMap::GetHashTableSize  
 确定地图的哈希表中的元素数。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 哈希表中的元素数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&57;](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>CMap::GetNextAssoc  
 检索处的地图元素`rNextPosition`，然后更新`rNextPosition`来指代映射中的下一个元素。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `rNextPosition`  
 指定对引用**位置**返回先前值`GetNextAssoc`或`GetStartPosition`调用。  
  
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
  
### <a name="example"></a>示例  
 请参阅示例[CMap::SetAt](#setat)。  
  
##  <a name="getsize"></a>CMap::GetSize  
 返回地图元素的数。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在映射中的项的数目。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索该映射中的元素数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&58; 页](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 通过返回启动映射迭代**位置**值，可以传递给`GetNextAssoc`调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，该值指示为循环映射; 的起始位置或**NULL**如果映射为空。  
  
### <a name="remarks"></a>备注  
 迭代序列是不可预测的;因此，"在映射中的第一个元素"有没有特别的意义。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::SetAt](#setat)。  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 初始化哈希表。  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUEÂ);  
```  
  
### <a name="parameters"></a>参数  
 `hashSize`  
 哈希表中的条目数。  
  
 `bAllocNow`  
 如果**TRUE**，分配的哈希表进行初始化; 否则在需要时分配的表。  
  
### <a name="remarks"></a>备注  
 为了获得最佳性能，哈希表大小应为质数。 为了尽量减少冲突，则大小应为大约 20%大于最大预期数据集。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::Lookup](#lookup)。  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 确定是否映射为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 此映射不包含任何元素; 如果非零值否则为 0。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::RemoveAll](#removeall)。  
  
##  <a name="lookup"></a>CMap::Lookup  
 查找映射到给定键的值。  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `ARG_KEY`  
 指定的类型的模板参数`key`值。  
  
 `key`  
 指定用于标识要查找的元素的键。  
  
 *值*  
 指定要查找的值的类型。  
  
 `rValue`  
 接收查阅到值。  
  
### <a name="return-value"></a>返回值  
 如果该元素; 如果未找到，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lookup`使用哈希算法来快速与给定的键完全匹配的键查找的地图元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&58; 页](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>CMap::operator]  
 方便代替`SetAt`成员函数。  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>参数  
 *值*  
 指定该映射值的类型的模板参数。  
  
 `ARG_KEY`  
 指定的密钥值的类型的模板参数。  
  
 `key`  
 用于从地图中检索值的键。  
  
### <a name="remarks"></a>备注  
 因此它可以使用仅在赋值语句 （左值） 的左侧。 如果没有地图元素与指定的键，则创建一个新的元素。  
  
 等效于此运算符的没有"右侧"（右值），因为一个密钥可能无法找到在映射中的可能性。 使用`Lookup`元素检索的成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::Lookup](#lookup)。  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 返回 map 对象的第一个条目。  
  
```  
const CPair* PGetFirstAssoc() const;Â CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>返回值  
 指向映射; 中的第一项的指针请参阅[CMap::CPair](#cpair)。 如果映射不包含任何项，则值是**NULL**。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回 map 对象中的第一个元素的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&59;](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 检索指向的位置的地图元素`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>参数  
 *pAssocRet*  
 指向返回先前的映射条目[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)调用。  
  
### <a name="return-value"></a>返回值  
 指针的映射; 中的下一个项目请参阅[CMap::CPair](#cpair)。 如果该元素是在映射中的最后一个，则值是**NULL**。  
  
### <a name="remarks"></a>备注  
 调用此方法来循环访问映射中的所有元素。 检索的第一个元素通过调用`PGetFirstAssoc`，然后循环访问具有对连续调用映射`PGetNextAssoc`。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>CMap::PLookup  
 查找映射到给定键的值。  
  
```  
const CPair* PLookup(ARG_KEY  key) const;
CPair* PLookup(Â    ARG_KEY  keyÂ);  ```  
  
### Parameters  
 `key`  
 Key for the element to be searched for.  
  
### Return Value  
 A pointer to a key structure; see [CMap::CPair](#cpair). If no match is found, `CMap::PLookup` returns `NULL`.  
  
### Remarks  
 Call this method to search for a map element with a key that exactly matches the given key.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 Removes all the values from this map by calling the global helper function **DestructElements**.  
  
```  
void RemoveAll();
```  
  
### Remarks  
 The function works correctly if the map is already empty.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 Looks up the map entry corresponding to the supplied key; then, if the key is found, removes the entry.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the key.  
  
 `key`  
 Key for the element to be removed.  
  
### Return Value  
 Nonzero if the entry was found and successfully removed; otherwise 0.  
  
### Remarks  
 The **DestructElements** helper function is used to remove the entry.  
  
### Example  
 See the example for [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>  CMap::SetAt  
 The primary means to insert an element in a map.  
  
```  
void SetAt (ARG_KEY 键、 ARG_VALUE newValue);
```  
  
### Parameters  
 `ARG_KEY`  
 Template parameter specifying the type of the `key` parameter.  
  
 `key`  
 Specifies the key of the new element.  
  
 `ARG_VALUE`  
 Template parameter specifying the type of the `newValue` parameter.  
  
 `newValue`  
 Specifies the value of the new element.  
  
### Remarks  
 First, the key is looked up. If the key is found, then the corresponding value is changed; otherwise a new key-value pair is created.  
  
### Example  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## See Also  
 [MFC Sample COLLECT](../../visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)  

