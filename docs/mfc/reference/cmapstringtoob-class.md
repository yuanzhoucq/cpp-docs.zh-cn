---
title: CMapStringToOb 类
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
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876369"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb 类

将唯一 `CString` 对象映射到 `CObject` 指针的字典集合类。

## <a name="syntax"></a>语法

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMapStringToOb：： CMapStringToOb](#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMapStringToOb：： GetCount](#getcount)|返回此映射中的元素数。|
|[CMapStringToOb：： GetHashTableSize](#gethashtablesize)|确定哈希表中元素的当前数目。|
|[CMapStringToOb：： GetNextAssoc](#getnextassoc)|获取用于循环访问的下一个元素。|
|[CMapStringToOb：： GetSize](#getsize)|返回此映射中的元素数。|
|[CMapStringToOb：： GetStartPosition](#getstartposition)|返回第一个元素的位置。|
|[CMapStringToOb：： HashKey](#hashkey)|计算指定键的哈希值。|
|[CMapStringToOb：： InitHashTable](#inithashtable)|初始化哈希表。|
|[CMapStringToOb：： IsEmpty](#isempty)|测试空映射条件（无元素）。|
|[CMapStringToOb：： Lookup](#lookup)|基于 void 指针键查找 void 指针。 指针值（而不是它指向的实体）用于键比较。|
|[CMapStringToOb：： LookupKey](#lookupkey)|返回对与指定键值关联的键的引用。|
|[CMapStringToOb：： RemoveAll](#removeall)|从此映射中移除所有元素。|
|[CMapStringToOb：： RemoveKey](#removekey)|移除由键指定的元素。|
|[CMapStringToOb：： SetAt](#setat)|将元素插入到映射中;如果找到匹配的键，则替换现有元素。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CMapStringToOb：： operator \[ \]](#operator_at)|将元素插入到映射中-用于 `SetAt`的运算符替换。|

## <a name="remarks"></a>备注

将 `CString`- `CObject*` 对（元素）插入到映射中后，可以使用字符串或 `CString` 值作为键来有效地检索或删除该对。 还可以循环访问映射中的所有元素。

"位置" 类型的变量用于所有地图变体中的替代入口访问。 您可以使用一个位置来 "记住" 一项，然后循环访问该映射。 您可能认为此迭代是按键值顺序进行的;不是。 检索到的元素的序列是不确定的。

`CMapStringToOb` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果使用重载的插入（ **<<** ）运算符或使用 `Serialize` 成员函数，则会依次序列化每个元素。

如果需要映射中单个元素（`CString` 值和 `CObject` 内容）的诊断转储，则必须将转储上下文的深度设置为1或更大。

删除 `CMapStringToOb` 对象或删除其元素时，将删除 `CString` 对象和 `CObject` 指针。 不会销毁 `CObject` 指针所引用的对象。

映射类派生类似于列表派生。 有关专用列表类的派生的说明，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

##  <a name="cmapstringtoob"></a>CMapStringToOb：： CMapStringToOb

构造空的 `CString`到 `CObject*` 映射。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
指定用于扩展映射的内存分配粒度。

### <a name="remarks"></a>备注

随着地图的增长，内存是以*nBlockSize*项的单位分配的。

下表显示了类似于 `CMapStringToOb:: CMapStringToOb`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr （INT_PTR** `nBlockSize` **= 10）;**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

##  <a name="getcount"></a>CMapStringToOb：： GetCount

确定地图中有多少元素。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

此图中的元素数。

### <a name="remarks"></a>备注

下表显示了类似于 `CMapStringToOb::GetCount`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>CMapStringToOb：： GetHashTableSize

确定哈希表中元素的当前数目。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>返回值

返回哈希表中的元素数。

### <a name="remarks"></a>备注

下表显示了类似于 `CMapStringToOb::GetHashTableSize`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize （） const;**|

##  <a name="getnextassoc"></a>CMapStringToOb：： GetNextAssoc

在*rNextPosition*中检索 map 元素，然后更新*rNextPosition*以引用映射中的下一个元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*rNextPosition*<br/>
指定对上一个 `GetNextAssoc` 或 `GetStartPosition` 调用返回的位置值的引用。

*rKey*<br/>
指定检索到的元素的返回键（字符串）。

*右值*<br/>
指定检索到的元素（`CObject` 指针）的返回值。 有关此参数的详细信息，请参阅 "备注"。

### <a name="remarks"></a>备注

此函数最适用于遍历映射中的所有元素。 请注意，位置序列不一定与键值序列相同。

如果检索到的元素是映射中的最后一个，则*rNextPosition*的新值将设置为 NULL。

对于*右*值参数，请确保将对象类型转换为**CObject\*&** ，这正是编译器需要的内容，如以下示例中所示：

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

对于基于模板的映射 `GetNextAssoc`，这种情况并不适用。

下表显示了类似于 `CMapStringToOb::GetNextAssoc`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，void\*&** *rKey* **，void\*&** *右***值） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，void\*&** *rKey* **，WORD &** *右***值） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，CString &** *rKey* **，void\*&** *右*值 **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，cstring &** *rKey* **，cstring &** *rValue* **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，WORD &** *rKey* **，CObject\*&** *右***值） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，WORD &** *rKey* **，void\*&** *右***值） const;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程序的结果如下所示：

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>CMapStringToOb：： GetSize

返回地图元素的数目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

映射中项的数目。

### <a name="remarks"></a>备注

调用此方法可检索映射中的元素数。

下表显示了类似于 `CMapStringToOb::GetSize`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>CMapStringToOb：： GetStartPosition

通过返回可传递给 `GetNextAssoc` 调用的位置值来启动映射迭代。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

一个位置值，该值指示循环访问映射的起始位置;如果映射为空，则为 NULL。

### <a name="remarks"></a>备注

迭代顺序不可预测;因此，"映射中的第一个元素" 没有特别的意义。

下表显示了类似于 `CMapStringToOb::GetStartPosition`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition （） const;**|

### <a name="example"></a>示例

请参阅[CMapStringToOb：： GetNextAssoc](#getnextassoc)的示例。

##  <a name="hashkey"></a>CMapStringToOb：： HashKey

计算指定键的哈希值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
要计算其哈希值的键。

### <a name="return-value"></a>返回值

密钥的哈希值

### <a name="remarks"></a>备注

下表显示了类似于 `CMapStringToOb::HashKey`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey （void** <strong>\*</strong> `key` **） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey （void** <strong>\*</strong> `key` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey （LPCTSTR** `key` **） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey （LPCTSTR** `key` **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey （WORD** `key` **） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey （WORD** `key` **） const;**|

##  <a name="inithashtable"></a>CMapStringToOb：： InitHashTable

初始化哈希表。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>参数

*hashSize*<br/>
哈希表中的项数。

*bAllocNow*<br/>
如果为 TRUE，则在初始化时分配哈希表;否则，将根据需要分配表。

### <a name="remarks"></a>备注

为了获得最佳性能，哈希表的大小应为质数。 若要最大程度地减少冲突，大小应大约比预期的最大数据集大20%。

下表显示了类似于 `CMapStringToOb::InitHashTable`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|

##  <a name="isempty"></a>CMapStringToOb：： IsEmpty

确定映射是否为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

如果此映射不包含任何元素，则为非零值;否则为0。

### <a name="example"></a>示例

请参阅[RemoveAll](#removeall)的示例。

### <a name="remarks"></a>备注

下表显示了类似于**CMapStringToOb：： IsEmpty**的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty （） const;**|

##  <a name="lookup"></a>CMapStringToOb：： Lookup

基于 `CString` 值返回 `CObject` 指针。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*key*<br/>
指定标识要查找的元素的字符串键。

*右值*<br/>
指定所查找元素中的返回值。

### <a name="return-value"></a>返回值

如果找到元素，则为非零值;否则为0。

### <a name="remarks"></a>备注

`Lookup` 使用哈希算法快速查找具有完全匹配的键（`CString` 值）的 map 元素。

下表显示了类似于 `CMapStringToOb::LookUp`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 查找（void** <strong>\*</strong> `key` **，void\*&** `rValue` **） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 查找（void** <strong>\*</strong> `key` **，WORD &** `rValue` **） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找（LPCTSTR** `key` **，void\*&** `rValue` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找（LPCTSTR** `key` **，CString &** `rValue` **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 查找（WORD** `key` **，CObject\*&** `rValue` **） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 查找（WORD** `key` **，void\*&** `rValue` **） const;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>CMapStringToOb：： LookupKey

返回对与指定键值关联的键的引用。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>参数

*key*<br/>
指定标识要查找的元素的字符串键。

*rKey*<br/>
对关联键的引用。

### <a name="return-value"></a>返回值

如果找到该键，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果在将关联的元素从映射中删除或映射被销毁后使用，则使用对该密钥的引用是不安全的。

下表显示了类似于 `CMapStringToOb:: LookupKey`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey （LPCTSTR** `key` **，LPCTSTR &** `rKey` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey （LPCTSTR** `key` **，LPCTSTR &** `rKey` **） const;**|

##  <a name="operator_at"></a>CMapStringToOb：： operator []

方便地替换 `SetAt` 成员函数。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>返回值

指向 `CObject` 对象的指针的引用;如果映射为空或*键*超出范围，则为 NULL。

### <a name="remarks"></a>备注

因此，它只能用于赋值语句的左侧（左值）。 如果没有具有指定键的 map 元素，则创建一个新元素。

没有与此运算符等效的 "右" （r 值），因为可能在映射中找不到键。 使用 `Lookup` 成员函数进行元素检索。

下表显示了类似于 `CMapStringToOb::operator []`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& 运算符\[] （void \*</strong> `key` **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & 运算符\[] （void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator\[] （lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & 运算符\[] （lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 运算符\[] （word** `key` **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& 运算符\[] （word** `key` **\);**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程序的结果如下所示：

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>CMapStringToOb：： RemoveAll

从此映射中移除所有元素并销毁 `CString` 的键对象。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

不会销毁每个键所引用的 `CObject` 对象。 如果不确保引用的 `CObject` 对象被销毁，则 `RemoveAll` 函数可能会导致内存泄漏。

如果映射已为空，则函数可以正常工作。

下表显示了类似于 `CMapStringToOb::RemoveAll`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll （）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll （）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll （）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll （）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll （）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>CMapStringToOb：： RemoveKey

查找与提供的键相对应的映射项;如果找到该密钥，则删除该条目。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于映射查找的字符串。

### <a name="return-value"></a>返回值

如果已找到并成功删除该项，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果未在其他位置删除 `CObject` 对象，这可能会导致内存泄漏。

下表显示了类似于 `CMapStringToOb::RemoveKey`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey （void** <strong>\*</strong> `key` **）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey （void** <strong>\*</strong> `key` **）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey （LPCTSTR** `key` **）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey （LPCTSTR** `key` **）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey （WORD** `key` **）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey （WORD** `key` **）;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程序的结果如下所示：

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>CMapStringToOb：： SetAt

在映射中插入元素的主要方法。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>参数

*key*<br/>
指定作为新元素的键的字符串。

*newValue*<br/>
指定 `CObject` 指针，该指针是新元素的值。

### <a name="remarks"></a>备注

首先，查找该密钥。 如果找到该键，则相应的值将更改;否则，将创建一个新的键/值元素。

下表显示了类似于 `CMapStringToOb::SetAt`的其他成员函数。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void SetAt （void** <strong>\*</strong> `key` **，void** <strong>\*</strong> `newValue` **）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void SetAt （void** <strong>\*</strong> `key` **，WORD** `newValue` **）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void SetAt （LPCTSTR** `key` **，void** <strong>\*</strong> `newValue` **）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void SetAt （LPCTSTR** `key` **，LPCTSTR** `newValue` **）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void SetAt （WORD** `key` **，CObject** <strong>\*</strong> `newValue` **）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void SetAt （WORD** `key` **，void** <strong>\*</strong> `newValue` **）;**|

### <a name="example"></a>示例

有关在所有集合示例中使用的 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

此程序的结果如下所示：

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
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 类](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString 类](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb 类](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)
