---
title: CMapStringtoOb 类
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 12de7bd72f643f08cebf948634703172d6725ce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370108"
---
# <a name="cmapstringtoob-class"></a>CMapStringtoOb 类

将唯一 `CString` 对象映射到 `CObject` 指针的字典集合类。

## <a name="syntax"></a>语法

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CmapStringToOb：：CmapstringtoOb](#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMapStringToOb：：获取计数](#getcount)|返回此映射中的元素数。|
|[CMapStringToOb：：获取哈希表大小](#gethashtablesize)|确定哈希表中的当前元素数。|
|[CMapStringToOb：：获取NextAssoc](#getnextassoc)|获取下一个迭代元素。|
|[CMapStringToOb：：获取大小](#getsize)|返回此映射中的元素数。|
|[CMapStringToOb：：获取起始位置](#getstartposition)|返回第一个元素的位置。|
|[CMapStringToOb：哈希基](#hashkey)|计算指定键的哈希值。|
|[CMapStringtoOb：：InithashTable](#inithashtable)|初始化哈希表。|
|[CMapStringToOb：：空](#isempty)|测试空映射条件（无元素）。|
|[CMapStringToOb：：查找](#lookup)|根据空指针键查找空指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapStringToOb：：查找键](#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapStringToOb：：删除所有](#removeall)|从此映射中删除所有元素。|
|[CMapStringToOb：：删除键](#removekey)|删除由键指定的元素。|
|[CMapStringToOb：：Setat](#setat)|将元素插入到地图中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CMapStringToOb：：运算符\[\]](#operator_at)|将元素插入到映射中 ， 运算符替换`SetAt`。|

## <a name="remarks"></a>备注

`CString`- 将`CObject*`对（元素）插入到地图中后，可以使用字符串或`CString`值作为键有效地检索或删除对。 您还可以迭代地图中的所有元素。

位置类型的变量用于所有地图变体中的备用条目访问。 您可以使用"位置"来"记住"条目并遍遍地图。 您可能认为此迭代按键值顺序;因此，您可以认为此迭代按键值顺序进行。它不是。 检索的元素的顺序不确定。

`CMapStringToOb` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果将地图存储到存档中（使用重载插入 （ **<<**） 运算符或使用`Serialize`成员函数，则依次序列化每个元素。

如果需要对地图中的各个元素（`CString`值和`CObject`内容）进行诊断转储，则必须将转储上下文的深度设置为 1 或更大。

删除`CMapStringToOb`对象或删除其元素时，`CString`将删除对象和`CObject`指针。 `CObject`指针引用的对象不会销毁。

映射类派生类似于列表派生。 有关特殊用途列表类派生的插图，请参阅文章["集合](../../mfc/collections.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CmapStringToOb：：CmapstringtoOb

构造空`CString`到`CObject*`映射。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
指定用于扩展映射的内存分配粒度。

### <a name="remarks"></a>备注

随着地图的增长，内存以*nBlockSize*条目的单位分配。

下表显示了与`CMapStringToOb:: CMapStringToOb`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrPtr（INT_PTR** `nBlockSize` **= 10）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapptrToWord（INT_PTR** `nBlockSize` **= 10 ）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringtoptr（INT_PTR** `nBlockSize` **= 10 ）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringtoString（INT_PTR** `nBlockSize` **= 10 ）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb（INT_PTR** `nBlockSize` **= 10 ）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**地图WordToptr（INT_PTR** `nBlockSize` **= 10 ）;**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb：：获取计数

确定地图中的元素数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

此映射中的元素数。

### <a name="remarks"></a>备注

下表显示了与`CMapStringToOb::GetCount`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR获取计数（ ） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR获取计数（ ） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR获取计数（ ） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR获取计数（ ） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR获取计数（ ） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR获取计数（ ） const;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb：：获取哈希表大小

确定哈希表中的当前元素数。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>返回值

返回哈希表中的元素数。

### <a name="remarks"></a>备注

下表显示了与`CMapStringToOb::GetHashTableSize`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT 获取哈希表尺寸 （ ） const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb：：获取NextAssoc

在*rNext定位*处检索地图元素，然后更新*rNext定位*以引用地图中的下一个元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*r 下一个位置*<br/>
指定对前`GetNextAssoc`一个或多个`GetStartPosition`调用返回的定位值的引用。

*rKey*<br/>
指定检索到的元素（字符串）的返回键。

*rValue*<br/>
指定检索到的元素（指针`CObject`）的返回值。 有关此参数的更多，请参阅备注。

### <a name="remarks"></a>备注

此函数对于迭代地图中的所有元素最有用。 请注意，位置序列不一定与键值序列相同。

如果检索到的元素是地图中的最后一个元素，则*rNext定位*的新值将设置为 NULL。

对于*rValue*参数，请确保将对象类型转换为**CObject\***，这是编译器所需的，如下例所示：

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

对于基于模板的地图`GetNextAssoc`，情况并非如此。

下表显示了与`CMapStringToOb::GetNextAssoc`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**空位 GetNextAssoc （位置&** *rNext位置***， 空\*** *rKey，* **空\*** *rValue）* **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空位 getNextAssoc （位置&** *rNext位置***， 空\*** 的*rKey，* WORD **&** *rValue）* **const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空位 GetNextAssoc （位置&** *rNext位置***， CString&** *rKey，* **空\*** *rValue）* **const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空位 getNextAssoc （位置&** *rNext位置***， CString&** *rKey，* **CString&** *rValue）* **const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空隙 getNextAssoc （位置&** *rNext位置***， WORD&** *rKey，* **CObject\* ** *rValue）* **const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空获取下一个位置（位置&** *rNext位置***，WORD&** *rKey，***空\*** 隙*rValue）* **const;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程序的结果如下：

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb：：获取大小

返回地图元素的数量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

地图中的项数。

### <a name="remarks"></a>备注

调用此方法以检索映射中的元素数。

下表显示了与`CMapStringToOb::GetSize`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR获取大小（ ） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR获取大小（ ） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR获取大小（ ） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR获取大小（ ） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR获取大小（ ） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR获取大小（ ） const;**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToOb：：获取起始位置

通过返回可以传递给`GetNextAssoc`调用的定位值来启动映射迭代。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

指示迭代地图的起始位置的定位值;如果地图为空，则为 NULL。

### <a name="remarks"></a>备注

迭代序列是不可预测的;因此，"地图中的第一个元素"没有特殊的意义。

下表显示了与`CMapStringToOb::GetStartPosition`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**位置获取起始位置（ ）**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**位置获取起始位置（ ）**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**位置获取起始位置（ ）**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**位置获取起始位置（ ）**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**位置获取起始位置（ ）**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**位置获取起始位置（ ）**|

### <a name="example"></a>示例

请参阅[CMapStringToOb 示例：获取NextAssoc](#getnextassoc)。

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb：哈希基

计算指定键的哈希值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>参数

*关键*<br/>
要计算哈希值的键。

### <a name="return-value"></a>返回值

密钥的哈希值

### <a name="remarks"></a>备注

下表显示了与`CMapStringToOb::HashKey`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT 哈希基 （ 空**<strong>\*</strong>`key` **） 康斯特;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT 哈希基 （ 空**<strong>\*</strong>`key` **） 康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT 哈希基 （ LPCTST** `key` **） 同;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT 哈希基 （ LPCTST** `key` **） 同;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**乌因特·哈什基（ WORD** `key` **） 康斯特;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**乌因特·哈什基（ WORD** `key` **） 康斯特;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringtoOb：：InithashTable

初始化哈希表。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>参数

*哈希*<br/>
哈希表中的条目数。

*巴洛克现在*<br/>
如果为 TRUE，则在初始化时分配哈希表;如果为 TRUE，则在初始化时分配哈希表。否则，将在需要时分配表。

### <a name="remarks"></a>备注

为了获得最佳性能，哈希表大小应为质数。 为了尽量减少冲突，大小应比最大预期数据集大大约 20%。

下表显示了与`CMapStringToOb::InitHashTable`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空因他表（UINT，** `hashSize` **BOOL** `bAllocNow` **= TRUE）;**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToOb：：空

确定地图是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此地图不包含任何元素，则非零;否则 0。

### <a name="example"></a>示例

请参阅[删除所有](#removeall)的示例。

### <a name="remarks"></a>备注

下表显示了与**CMapStringToOb：： isempty**类似的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 是空的（ ） 康斯特;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 是空的（ ） 康斯特;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb：：查找

返回基于`CObject`值的`CString`指针。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*关键*<br/>
指定标识要备份的元素的字符串键。

*rValue*<br/>
指定从上找元素返回的值。

### <a name="return-value"></a>返回值

如果找到元素，则非零;否则 0。

### <a name="remarks"></a>备注

`Lookup`使用哈希算法快速查找具有与 （`CString`值） 完全匹配的键的映射元素。

下表显示了与`CMapStringToOb::LookUp`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 查找（无效**<strong>\*</strong>`key`**、无效\***`rValue`**） 同流;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 查找（空，WORD** <strong>\*</strong> `key` **&）** `rValue` **同一点;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找（LPCTSTR，** `key` **\*空**`rValue`**） 同;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找（LPCTSTR，CString** `key` **&）** `rValue` **康斯特;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 查找（WORD、** `key` **\* CObject）** `rValue` **同一点;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 查找（WORD，** `key` **\*空**`rValue`**） 康斯特;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb：：查找键

返回对与指定键值关联的键的引用。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>参数

*关键*<br/>
指定标识要备份的元素的字符串键。

*rKey*<br/>
对关联密钥的引用。

### <a name="return-value"></a>返回值

如果找到密钥，则非零;否则 0。

### <a name="remarks"></a>备注

如果在从地图中删除关联元素后或地图被销毁后使用对键的引用，则使用引用密钥不安全。

下表显示了与`CMapStringToOb:: LookupKey`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找键（LPCTSTR，LPCTSTR** `key` **&）** `rKey` **康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找键（LPCTSTR，LPCTSTR** `key` **&）** `rKey` **康斯特;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb：：运算符 |

成员函数的`SetAt`方便替代品。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>返回值

对指向对象的指针的`CObject`引用;对对象的引用如果地图为空或*键*范围不范围，则为 NULL。

### <a name="remarks"></a>备注

因此，它只能在赋值语句（l 值）的左侧使用。 如果没有具有指定键的地图元素，则创建新元素。

没有等效于此运算符的"右侧"（r 值），因为在地图中可能找不到键。 使用`Lookup`成员函数进行元素检索。

下表显示了与`CMapStringToOb::operator []`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>无效\*&运算符\[*（\*无效</strong>`key`**\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD&\[运算符 *（无效**<strong>\*</strong>`key`**\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空\*&运算符\[*（lpctstr** `key` ** \);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString&运算符\[_（lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject&\*运算符\[_（单词**`key`**\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**无效\*&运算符\[*（字**`key`**\);**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程序的结果如下：

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb：：删除所有

从此映射中删除所有元素并销毁`CString`关键对象。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

不会`CObject`销毁每个键引用的对象。 如果不`RemoveAll`确保引用`CObject`的对象被销毁，则该函数可能会导致内存泄漏。

如果地图已为空，则函数工作正常。

下表显示了与`CMapStringToOb::RemoveAll`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**无效删除所有（ ）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**无效删除所有（ ）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**无效删除所有（ ）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**无效删除所有（ ）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**无效删除所有（ ）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**无效删除所有（ ）;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb：：删除键

查找与提供的键对应的地图条目;然后，如果找到该键，则删除该条目。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>参数

*关键*<br/>
指定用于地图查找的字符串。

### <a name="return-value"></a>返回值

如果发现并成功删除条目，则非零;否则 0。

### <a name="remarks"></a>备注

如果未在其他地方删除对象，`CObject`则可能导致内存泄漏。

下表显示了与`CMapStringToOb::RemoveKey`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 删除键（空**<strong>\*</strong>`key`**）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 删除键（空**<strong>\*</strong>`key`**）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 删除键 （ LPCTSTR** `key` **）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 删除键 （ LPCTSTR** `key` **）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 删除键 （WORD）;** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 删除键 （WORD）;** `key` **);**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程序的结果如下：

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToOb：：Setat

主要是指在地图中插入元素。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>参数

*关键*<br/>
指定作为新元素键的字符串。

*新值*<br/>
指定`CObject`作为新元素值的指针。

### <a name="remarks"></a>备注

首先，键被抬起来。 如果找到该键，则更改相应的值;如果找到该键，则更改相应的值。否则将创建新的键值元素。

下表显示了与`CMapStringToOb::SetAt`的其他成员函数类似的。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**无效（无效**<strong>\*</strong>`key`**，无效**<strong>\*</strong>`newValue`**）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空设置（空**<strong>\*</strong>`key`**，WORD）;** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空位（LPCTSTR，** `key`**空**<strong>\*</strong>`newValue`**）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空集（LPCTSTR，LPCTSTR）;** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空集（WORD，** `key` **Cobject）;** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空集（WORD，** `key`**空**<strong>\*</strong>`newValue`**）;**|

### <a name="example"></a>示例

有关所有集合示例中使用的类的列表，`CAge`请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

此程序的结果如下：

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrPtr 类](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringtoString 类](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb 类](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)
