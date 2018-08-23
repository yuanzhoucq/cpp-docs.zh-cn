---
title: CMap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebfacd93c8a346c2303e80ded4e28f3314ed10bb
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339164"
---
# <a name="cmap-class"></a>CMap 类
将唯一键映射到值的字典集合类。  
  
## <a name="syntax"></a>语法  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>参数  
 *KEY*  
 用作映射的键的对象的类。  
  
 *ARG_KEY*  
 用于数据类型*键*自变量; 通常指*密钥*。  
  
 *值*  
 在映射中存储的对象的类。  
  
 *ARG_VALUE*  
 用于数据类型*值*自变量; 通常指*值*。  
  
## <a name="members"></a>成员  
  
### <a name="public-structures"></a>公共结构  
  
|name|描述|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|包含密钥值和关联的对象的值的嵌套的结构。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|构造一个集合，其中将键映射到值。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|此映射中返回元素的数。|  
|[CMap::GetHashTableSize](#gethashtablesize)|哈希表中返回元素的数。|  
|[CMap::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|  
|[CMap::GetSize](#getsize)|此映射中返回元素的数。|  
|[CMap::GetStartPosition](#getstartposition)|返回第一个元素的位置。|  
|[CMap::InitHashTable](#inithashtable)|初始化哈希表，并指定其大小。|  
|[CMap::IsEmpty](#isempty)|空映射条件 （元素） 的测试。|  
|[CMap::Lookup](#lookup)|查找映射到给定键的值。|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|返回指向第一个元素的指针。|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|获取一个指向下一个元素的迭代。|  
|[CMap::PLookup](#plookup)|返回一个指向其值与指定的值匹配的键。|  
|[CMap::RemoveAll](#removeall)|此映射中移除所有元素。|  
|[CMap::RemoveKey](#removekey)|移除由键指定的元素。|  
|[CMap::SetAt](#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CMap::operator]](#operator_at)|将元素插入到映射 — 运算符替换为`SetAt`。|  
  
## <a name="remarks"></a>备注  
 一旦已插入到映射的键 / 值对 （元素），可以有效地检索或删除使用该密钥来访问它的对。 此外可以循环访问映射中的所有元素。  
  
 位置使用备用访问项类型的变量。 可以使用位置"记住"条目并循环访问映射。 您可能认为此迭代是有顺序的键值;不是这样。 检索元素的序列是不确定。  
  
 全局帮助器函数的此类调用的某些成员函数必须进行自定义的大部分使用`CMap`类。 请参阅[集合类帮助器](../../mfc/reference/collection-class-helpers.md)中的宏和全局函数部分**MFC 参考**。  
  
 `CMap` 重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)以支持序列化和转储的它的元素。 如果映射存储到存档使用`Serialize`，反过来序列化每个地图元素。 默认实现`SerializeElements`帮助程序函数执行按位写入。 有关指针集合项的序列化信息派生自`CObject`或其他用户定义的类型，请参阅[如何： 创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  
  
 如果您需要映射 （密钥和值） 中的各个元素的诊断转储，必须将转储上下文的深度设置为 1 或更高版本。  
  
 当`CMap`对象被删除，或删除它的元素，删除密钥和值。  
  
 映射类派生是类似于列表派生。 请参阅文章[集合](../../mfc/collections.md)有关的特殊用途的列表类派生的图例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="cmap"></a>  CMap::CMap  
 构造空映射。  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 *nBlockSize*  
 指定扩展映射的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 随着映射中的单元分配内存*nBlockSize*条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>  CMap::CPair  
 包含密钥值和关联的对象的值。  
  
### <a name="remarks"></a>备注  
 这是一个类中的嵌套的结构[CMap](../../mfc/reference/cmap-class.md)。  
  
 该结构由两个字段组成：  
  
- `key` 密钥类型的实际值。  
  
- `value` 关联的对象的值。  
  
 它用于存储中的返回值[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，并[CMap::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>示例  
 有关用法的示例，请参阅示例[CMap::PLookup](#plookup)。  
  
##  <a name="getcount"></a>  CMap::GetCount  
 检索映射中的元素数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 元素数量。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::Lookup](#lookup)。  
  
##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize  
 确定地图的哈希表中的元素数。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 哈希表中的元素数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>  CMap::GetNextAssoc  
 检索处的地图元素`rNextPosition`，然后更新`rNextPosition`来指代在映射中的下一个元素。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 *rNextPosition*  
 指定对先前返回的位置值的引用`GetNextAssoc`或`GetStartPosition`调用。  
  
 *KEY*  
 指定地图的键的类型的模板参数。  
  
 *rKey*  
 指定返回检索到的元素的键。  
  
 *值*  
 指定地图的值的类型的模板参数。  
  
 *rValue*  
 指定检索的元素的返回的值。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于通过映射中的所有元素。 请注意，位置序列不一定与密钥值序列相同。  
  
 如果检索的元素在映射中上, 一次然后的新值*rNextPosition*设置为 NULL。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::SetAt](#setat)。  
  
##  <a name="getsize"></a>  CMap::GetSize  
 返回地图元素的数。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在映射中的项的数目。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索该映射中的元素数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CMap::GetStartPosition  
 通过返回位置值，可传递给启动映射迭代`GetNextAssoc`调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 位置值，该值指示用于循环访问映射的起始位置或者，如果映射为空，则为 NULL。  
  
### <a name="remarks"></a>备注  
 迭代序列不是可预测;因此，"映射中的第一个元素"有没有特别的意义。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::SetAt](#setat)。  
  
##  <a name="inithashtable"></a>  CMap::InitHashTable  
 初始化哈希表。  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>参数  
 *hashSize*  
 哈希表中的条目数。  
  
 *bAllocNow*  
 如果为 TRUE，则会分配哈希表初始化; 时否则需要时分配的表。  
  
### <a name="remarks"></a>备注  
 为了获得最佳性能，哈希表大小应为一个素数。 为了尽量减少冲突，大小应为大约 20%超过最大预期的数据集。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::Lookup](#lookup)。  
  
##  <a name="isempty"></a>  CMap::IsEmpty  
 确定是否映射为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 此映射不包含任何元素; 如果非零值否则为 0。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::RemoveAll](#removeall)。  
  
##  <a name="lookup"></a>  CMap::Lookup  
 查找映射到给定键的值。  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 *ARG_KEY*  
 指定的类型的模板参数*密钥*值。  
  
 *key*  
 指定用于标识要查找的元素的键。  
  
 *值*  
 指定要查找的值的类型。  
  
 *rValue*  
 接收的查找值。  
  
### <a name="return-value"></a>返回值  
 如果找到该元素; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lookup` 使用哈希算法来快速查找与给定的键完全匹配的密钥的地图元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>  CMap::operator]  
 便捷替代`SetAt`成员函数。  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>参数  
 *值*  
 指定该映射值的类型的模板参数。  
  
 *ARG_KEY*  
 模板参数指定的密钥值的类型。  
  
 *key*  
 用于从地图中检索值的键。  
  
### <a name="remarks"></a>备注  
 因此它可以仅在左侧和右侧的赋值语句 （左值） 上使用。 如果不存在具有指定键映射元素，则会创建一个新的元素。  
  
 没有等效于此运算符的任何"右侧"（右值），因为可能可能映射中找到密钥。 使用`Lookup`元素检索的成员函数。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::Lookup](#lookup)。  
  
##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc  
 返回 map 对象的第一个条目。  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>返回值  
 指向映射中的第一个条目请参阅[CMap::CPair](#cpair)。 如果映射不包含任何条目，则该值为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回 map 对象中的第一个元素的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc  
 检索指向的位置的地图元素*pAssocRec*。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>参数  
 *pAssocRet*  
 指向返回先前的映射条目[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)调用。  
  
### <a name="return-value"></a>返回值  
 指向映射中，则在下一个条目请参阅[CMap::CPair](#cpair)。 如果该元素为在映射中的最后一个，该值为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法来循环访问映射中的所有元素。 检索的第一个元素通过调用`PGetFirstAssoc`，然后循环访问具有连续调用映射`PGetNextAssoc`。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>  CMap::PLookup  
 查找映射到给定键的值。  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>参数  
 *key*  
 若要在其中搜索的元素键。  
  
### <a name="return-value"></a>返回值  
 指向密钥结构;请参阅[CMap::CPair](#cpair)。 如果不找到任何匹配项，则`CMap::PLookup`返回 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法搜索的地图元素与给定的键完全匹配的密钥。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 此映射中删除所有值，通过调用全局帮助器函数`DestructElements`。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 功能工作正常，如果映射已经为空。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>  CMap::RemoveKey  
 查找映射条目对应于所提供的密钥;然后，如果找到该键，则移除的项。  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>参数  
 *ARG_KEY*  
 指定的键类型模板参数。  
  
 *key*  
 要移除的元素键。  
  
### <a name="return-value"></a>返回值  
 如果找到该条目并将其成功移除，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `DestructElements`帮助器函数用于删除的条目。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMap::SetAt](#setat)。  
  
##  <a name="setat"></a>  CMap::SetAt  
 主要方法要在地图中插入元素。  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>参数  
 *ARG_KEY*  
 指定的类型的模板参数*密钥*参数。  
  
 *key*  
 指定新元素的键。  
  
 *ARG_VALUE*  
 指定的类型的模板参数*newValue*参数。  
  
 *newValue*  
 指定新元素的值。  
  
### <a name="remarks"></a>备注  
 首先，查找密钥。 如果找到该键，然后更改相应的值;否则创建一个新的键-值对。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)  
