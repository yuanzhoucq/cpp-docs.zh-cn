---
title: CMap 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd7c1b23e3c586bf89a86e17d85ee5b5050fbf37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 数据类型用于`KEY`自变量; 通常指`KEY`。  
  
 `VALUE`  
 存储在映射中的对象类。  
  
 `ARG` *_* `VALUE`  
 数据类型用于`VALUE`自变量; 通常指`VALUE`。  
  
## <a name="members"></a>成员  
  
### <a name="public-structures"></a>公共结构  
  
|name|描述|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|一个包含密钥值和关联的对象的值的嵌套的结构。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|构造键映射到值的集合。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|在此地图中返回元素的数。|  
|[CMap::GetHashTableSize](#gethashtablesize)|返回哈希表中的元素数。|  
|[CMap::GetNextAssoc](#getnextassoc)|获取循环的下一个元素。|  
|[CMap::GetSize](#getsize)|在此地图中返回元素的数。|  
|[CMap::GetStartPosition](#getstartposition)|返回的第一个元素的位置。|  
|[CMap::InitHashTable](#inithashtable)|初始化哈希表，并指定其大小。|  
|[CMap::IsEmpty](#isempty)|空映射条件 （没有元素） 的测试。|  
|[CMap::Lookup](#lookup)|查找映射到给定键的值。|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|返回指向第一个元素的指针。|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|获取一个指向下一个元素的循环。|  
|[CMap::PLookup](#plookup)|将指针返回到其值与指定的值匹配的键。|  
|[CMap::RemoveAll](#removeall)|从此映射中移除所有元素。|  
|[CMap::RemoveKey](#removekey)|移除由键指定的元素。|  
|[CMap::SetAt](#setat)|将元素插入到映射;如果找到匹配的键，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::operator]](#operator_at)|将元素插入到映射 — 运算符替换`SetAt`。|  
  
## <a name="remarks"></a>备注  
 一旦已插入到映射的键 / 值对 （元素），你可以高效地检索或删除使用该密钥来访问它的对。 此外可以循环访问映射中的所有元素。  
  
 类型的变量的**位置**用于对项的备用访问。 你可以使用**位置**"记住"条目和循环通过映射。 你可能会认为此迭代是根据键值; 顺序不存在。 检索元素的序列是不确定的。  
  
 全局帮助器函数，此类调用某些成员函数必须进行自定义的大部分使用`CMap`类。 请参阅[集合类帮助器](../../mfc/reference/collection-class-helpers.md)中的宏和全局函数部分`MFC Reference`。  
  
 `CMap`重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)用于支持序列化和转储的其元素。 如果映射存储到存档使用`Serialize`，每个地图元素将依次序列化。 默认实现`SerializeElements`帮助器函数执行的位写入。 有关指针集合项的序列化信息派生自`CObject`或其他用户定义类型，请参阅[如何： 创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果你需要映射 （键和值） 中的各个元素的诊断转储，你必须设置为 1 或更高版本的转储上下文的深度。  
  
 当`CMap`对象被删除，或时删除其元素，键和值都将被删除。  
  
 映射类派生是类似于列表派生。 请参阅文章[集合](../../mfc/collections.md)有关特殊用途列表类派生的图例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>惠?  
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
 随着映射后，内存分配的单位`nBlockSize`条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 包含一个密钥值和关联的对象的值。  
  
### <a name="remarks"></a>备注  
 这是在类中的嵌套的结构[CMap](../../mfc/reference/cmap-class.md)。  
  
 结构组成两个字段：  
  
- **密钥**与键类型的实际值。  
  
- **值**关联的对象的值。  
  
 它用于存储中的返回值[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，和[CMap::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>示例  
 有关用法的一个示例，请参阅示例[CMap::PLookup](#plookup)。  
  
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
 确定地图哈希表中的元素数。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 哈希表中的元素数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>CMap::GetNextAssoc  
 检索处的地图元素`rNextPosition`，然后更新`rNextPosition`来引用映射中的下一个元素。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `rNextPosition`  
 指定对引用**位置**通过前一个返回值`GetNextAssoc`或`GetStartPosition`调用。  
  
 *KEY*  
 指定地图的键的类型的模板参数。  
  
 `rKey`  
 指定检索的元素返回的密钥。  
  
 *值*  
 指定地图的值的类型的模板参数。  
  
 `rValue`  
 指定检索的元素的返回的值。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于循环访问映射中的所有元素。 请注意，位置序列不一定是相同的密钥值序列。  
  
 如果检索的元素的是在映射中，最后然后的新值`rNextPosition`设置为**NULL**。  
  
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
 调用此方法以检索在映射中的元素的数目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 通过返回启动映射迭代**位置**值，可以传递给`GetNextAssoc`调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**值，该值指示来循环映射; 的起始位置或**NULL**如果映射为空。  
  
### <a name="remarks"></a>备注  
 迭代序列是不可预测的;因此，"映射中的第一个元素"必须没有特别的意义。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::SetAt](#setat)。  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 初始化哈希表。  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>参数  
 `hashSize`  
 哈希表中的条目数。  
  
 `bAllocNow`  
 如果**TRUE**，分配哈希表初始化; 在需要时否则分配表。  
  
### <a name="remarks"></a>备注  
 为了获得最佳性能，哈希表大小应为质数。 为了尽量减少冲突，则大小应为大致大于最大预期的数据集的 20%。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::Lookup](#lookup)。  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 确定是否映射为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此映射不包含任何元素; 则为非 0否则为 0。  
  
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
 指定标识要查找的元素的键。  
  
 *值*  
 指定要查找的值的类型。  
  
 `rValue`  
 接收的查阅到值。  
  
### <a name="return-value"></a>返回值  
 如果该元素; 如果未找到则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lookup`使用哈希算法来快速查找与给定的键完全匹配的密钥的地图元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>CMap::operator]  
 一个方便替换`SetAt`成员函数。  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>参数  
 *值*  
 指定的映射值的类型的模板参数。  
  
 `ARG_KEY`  
 指定的密钥值的类型的模板参数。  
  
 `key`  
 用于从映射中检索的值的键。  
  
### <a name="remarks"></a>备注  
 因此它可以仅在赋值语句 （左值） 的左侧使用。 如果没有地图元素与指定的键，则会创建一个新的元素。  
  
 没有等效于此运算符的任何"右侧"（右值），因为一个密钥可能无法找到在映射中的可能。 使用`Lookup`元素检索的成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::Lookup](#lookup)。  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 返回 map 对象的第一个条目。  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>返回值  
 指向映射; 中的第一个条目请参阅[CMap::CPair](#cpair)。 如果映射不包含任何项，则值是**NULL**。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回 map 对象中的第一个元素的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 检索指向的地图元素`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>参数  
 *pAssocRet*  
 指向先前返回一个映射条目[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)调用。  
  
### <a name="return-value"></a>返回值  
 指向映射; 中的下一个条目请参阅[CMap::CPair](#cpair)。 如果该元素为地图中的最后一个，则值是**NULL**。  
  
### <a name="remarks"></a>备注  
 调用此方法以循环访问映射中的所有元素。 检索通过调用的第一个元素`PGetFirstAssoc`，然后循环访问映射到的连续调用`PGetNextAssoc`。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>CMap::PLookup  
 查找映射到给定键的值。  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 要搜索的元素键。  
  
### <a name="return-value"></a>返回值  
 指向密钥结构;请参阅[CMap::CPair](#cpair)。 如果不找到任何匹配项，则`CMap::PLookup`返回`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此方法可搜索的地图元素与给定的键完全匹配的密钥。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>CMap::RemoveAll  
 从此映射中移除所有的值，通过调用全局帮助器函数**DestructElements**。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果映射已经为空，该函数能正常工作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>CMap::RemoveKey  
 查找与提供的键; 相对应的映射条目然后，如果找到该键中, 移除的项。  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>参数  
 `ARG_KEY`  
 指定的键类型的模板参数。  
  
 `key`  
 要移除的元素键。  
  
### <a name="return-value"></a>返回值  
 如果该条目已成功找到并移除; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 **DestructElements**帮助器函数用于删除的项。  
  
### <a name="example"></a>示例  
 请参阅示例[CMap::SetAt](#setat)。  
  
##  <a name="setat"></a>CMap::SetAt  
 主要方法将一个元素插入映射中。  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>参数  
 `ARG_KEY`  
 指定的类型的模板参数`key`参数。  
  
 `key`  
 指定新元素的键。  
  
 `ARG_VALUE`  
 指定的类型的模板参数`newValue`参数。  
  
 `newValue`  
 指定新的元素的值。  
  
### <a name="remarks"></a>备注  
 首先，查找键。 如果找到该键，则相应的值发生更改;否则创建一个新的键 / 值对。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)  
