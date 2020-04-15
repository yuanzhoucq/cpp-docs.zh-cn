---
title: CMap 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 9a3c92a0a8c3d40e4cc3d289cc0221ff7cdb2e11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370098"
---
# <a name="cmap-class"></a>CMap 类

将唯一键映射到值的字典集合类。

## <a name="syntax"></a>语法

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>参数

*关键*<br/>
用作映射键的对象的类。

*ARG_KEY*<br/>
用于*KEY*参数的数据类型;通常引用*KEY*。

*价值*<br/>
存储在地图中的对象的类。

*ARG_VALUE*<br/>
用于*VALUE*参数的数据类型;通常引用*VALUE*。

## <a name="members"></a>成员

### <a name="public-structures"></a>公共结构

|名称|说明|
|----------|-----------------|
|[CMap：CPair](#cpair)|包含键值和关联对象值的嵌套结构。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMap：CMap](#cmap)|构造将键映射到值的集合。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMap：获取计数](#getcount)|返回此映射中的元素数。|
|[CMap：获取哈希表大小](#gethashtablesize)|返回哈希表中的元素数。|
|[CMap：获取NextAssoc](#getnextassoc)|获取下一个迭代元素。|
|[CMap：获取大小](#getsize)|返回此映射中的元素数。|
|[CMap：获取起始位置](#getstartposition)|返回第一个元素的位置。|
|[CMap：inithashTable](#inithashtable)|初始化哈希表并指定其大小。|
|[CMap：：空](#isempty)|测试空映射条件（无元素）。|
|[CMap：：查找](#lookup)|查找映射到给定键的值。|
|[CMap：:P获取第一Assoc](#pgetfirstassoc)|返回指向第一个元素的指针。|
|[CMap：:P获取NextAssoc](#pgetnextassoc)|获取指向下一个元素的指针，以便迭代。|
|[CMap：:P查找](#plookup)|返回指向其值与指定值匹配的键的指针。|
|[CMap：：全部删除](#removeall)|从此映射中删除所有元素。|
|[CMap：：删除键](#removekey)|删除由键指定的元素。|
|[CMap：setat](#setat)|将元素插入到地图中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMap：：运算符\[\]](#operator_at)|将元素插入到映射中 ， 运算符替换`SetAt`。|

## <a name="remarks"></a>备注

将键值对（元素）插入到地图中后，可以使用该键有效地检索或删除该对。 您还可以迭代地图中的所有元素。

位置类型的变量用于对条目的备用访问。 您可以使用"位置"来"记住"条目并遍遍地图。 您可能认为此迭代按键值顺序;因此，您可以认为此迭代按键值顺序进行。它不是。 检索的元素的顺序不确定。

此类的某些成员函数调用全局帮助器函数，这些函数必须针对`CMap`类的大多数用途进行自定义。 请参阅**MFC 参考**的宏和全局部分中的[集合类帮助器](../../mfc/reference/collection-class-helpers.md)。

`CMap`覆盖[CObject：：序列化](../../mfc/reference/cobject-class.md#serialize)以支持其元素的序列化和转储。 如果使用 将地图存储到存档`Serialize`，则依次序列化每个地图元素。 帮助器函数的`SerializeElements`默认实现执行位写入。 有关派生自`CObject`或其他用户定义的类型的指针集合项的序列化的信息，请参阅[如何：创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。

如果需要对地图中的各个元素（键和值）进行诊断转储，则必须将转储上下文的深度设置为 1 或更大。

删除`CMap`对象或删除其元素时，将删除键和值。

映射类派生类似于列表派生。 有关特殊用途列表类派生的插图，请参阅文章["集合](../../mfc/collections.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>要求

**标头：** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap：CMap

构造空地图。

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
指定用于扩展映射的内存分配粒度。

### <a name="remarks"></a>备注

随着地图的增长，内存以*nBlockSize*条目的单位分配。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap：CPair

包含键值和关联对象的值。

### <a name="remarks"></a>备注

这是类[CMap](../../mfc/reference/cmap-class.md)中的嵌套结构。

结构由两个字段组成：

- `key`键类型的实际值。

- `value`关联对象的值。

它用于存储[从 CMap：:P 查找](#plookup)[、CMap：:PGetFirstAssoc](#pgetfirstassoc)和[CMap：:PGetNextAssoc](#pgetnextassoc)的返回值。

### <a name="example"></a>示例

有关使用情况的示例，请参阅[CMap：:P 查找"的示例](#plookup)。

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap：获取计数

检索地图中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

元素数量。

### <a name="example"></a>示例

请参阅[CMap：：查找](#lookup)的示例。

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap：获取哈希表大小

确定地图哈希表中的元素数。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>返回值

哈希表中的元素数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap：获取NextAssoc

在 中检索地图元素`rNextPosition`，然后更新`rNextPosition`以引用地图中的下一个元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*r 下一个位置*<br/>
指定对前`GetNextAssoc`一个或多个`GetStartPosition`调用返回的定位值的引用。

*关键*<br/>
指定地图键类型的模板参数。

*rKey*<br/>
指定检索到的元素的返回键。

*价值*<br/>
指定地图值类型的模板参数。

*rValue*<br/>
指定检索到的元素的返回值。

### <a name="remarks"></a>备注

此函数对于迭代地图中的所有元素最有用。 请注意，位置序列不一定与键值序列相同。

如果检索到的元素是地图中的最后一个元素，则*rNext定位*的新值将设置为 NULL。

### <a name="example"></a>示例

请参阅[CMap：：setAt](#setat)的示例。

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap：获取大小

返回地图元素的数量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

地图中的项数。

### <a name="remarks"></a>备注

调用此方法以检索映射中的元素数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap：获取起始位置

通过返回可以传递给`GetNextAssoc`调用的定位值来启动映射迭代。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

指示迭代地图的起始位置的定位值;如果地图为空，则为 NULL。

### <a name="remarks"></a>备注

迭代序列是不可预测的;因此，"地图中的第一个元素"没有特殊的意义。

### <a name="example"></a>示例

请参阅[CMap：：setAt](#setat)的示例。

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap：inithashTable

初始化哈希表。

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>参数

*哈希*<br/>
哈希表中的条目数。

*巴洛克现在*<br/>
如果为 TRUE，则在初始化时分配哈希表;如果为 TRUE，则在初始化时分配哈希表。否则，将在需要时分配表。

### <a name="remarks"></a>备注

为了获得最佳性能，哈希表大小应为质数。 为了尽量减少冲突，大小应比最大预期数据集大大约 20%。

### <a name="example"></a>示例

请参阅[CMap：：查找](#lookup)的示例。

## <a name="cmapisempty"></a><a name="isempty"></a>CMap：：空

确定地图是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此地图不包含任何元素，则非零;否则 0。

### <a name="example"></a>示例

请参阅[CMap 示例：：删除所有](#removeall)。

## <a name="cmaplookup"></a><a name="lookup"></a>CMap：：查找

查找映射到给定键的值。

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>参数

*ARG_KEY*<br/>
指定*键*值类型的模板参数。

*关键*<br/>
指定标识要备份的元素的键。

*价值*<br/>
指定要抬头的值的类型。

*rValue*<br/>
接收上个值。

### <a name="return-value"></a>返回值

如果找到元素，则非零;否则 0。

### <a name="remarks"></a>备注

`Lookup`使用哈希算法快速查找具有与给定键完全匹配的键的映射元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap：：运算符 |

成员函数的`SetAt`方便替代品。

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>参数

*价值*<br/>
指定地图值类型的模板参数。

*ARG_KEY*<br/>
指定键值类型的模板参数。

*关键*<br/>
用于从映射检索值的键。

### <a name="remarks"></a>备注

因此，它只能在赋值语句（l 值）的左侧使用。 如果没有具有指定键的地图元素，则创建新元素。

没有等效于此运算符的"右侧"（r 值），因为在地图中可能找不到键。 使用`Lookup`成员函数进行元素检索。

### <a name="example"></a>示例

请参阅[CMap：：查找](#lookup)的示例。

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap：:P获取第一Assoc

返回地图对象的第一个条目。

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>返回值

指向地图中第一个条目的指针;请参阅[CMap：CPair](#cpair)。 如果地图不包含条目，则值为 NULL。

### <a name="remarks"></a>备注

调用此函数以返回地图对象中第一个元素的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap：:P获取NextAssoc

检索*由 pAssocRec*指向的地图元素。

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>参数

*帕索克雷特*<br/>
指向以前[PGetNextAssoc](#pgetnextassoc)或[CMap：:PGetFirstAssoc](#pgetfirstassoc)调用返回的地图条目。

### <a name="return-value"></a>返回值

指向地图中下一个条目的指针;请参阅[CMap：CPair](#cpair)。 如果元素是地图中的最后一个元素，则该值为 NULL。

### <a name="remarks"></a>备注

调用此方法以迭代地图中的所有元素。 使用 调用`PGetFirstAssoc`检索第一个元素，然后通过映射遍历对`PGetNextAssoc`的调用来迭代。

### <a name="example"></a>示例

请参阅[CMap：:P获取第一Assoc](#pgetfirstassoc)的示例。

## <a name="cmapplookup"></a><a name="plookup"></a>CMap：:P查找

查找映射到给定键的值。

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>参数

*关键*<br/>
要搜索的元素的键。

### <a name="return-value"></a>返回值

指向键结构的指针;指向键结构的指针请参阅[CMap：CPair](#cpair)。 如果未找到匹配项，`CMap::PLookup`则返回 NULL。

### <a name="remarks"></a>备注

调用此方法以搜索具有与给定键完全匹配的键的地图元素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap：：全部删除

通过调用全局帮助器函数`DestructElements`从此映射中删除所有值。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

如果地图已为空，则函数工作正常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap：：删除键

查找与提供的键对应的地图条目;然后，如果找到该键，则删除该条目。

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>参数

*ARG_KEY*<br/>
指定键类型的模板参数。

*关键*<br/>
要删除的元素的键。

### <a name="return-value"></a>返回值

如果发现并成功删除条目，则非零;否则 0。

### <a name="remarks"></a>备注

帮助`DestructElements`器函数用于删除条目。

### <a name="example"></a>示例

请参阅[CMap：：setAt](#setat)的示例。

## <a name="cmapsetat"></a><a name="setat"></a>CMap：setat

主要是指在地图中插入元素。

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>参数

*ARG_KEY*<br/>
指定*键*参数类型的模板参数。

*关键*<br/>
指定新元素的键。

*ARG_VALUE*<br/>
指定*newValue*参数类型的模板参数。

*新值*<br/>
指定新元素的值。

### <a name="remarks"></a>备注

首先，键被抬起来。 如果找到该键，则更改相应的值;如果找到该键，则更改相应的值。否则将创建新的键值对。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
