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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253044"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb 类

将唯一 `CString` 对象映射到 `CObject` 指针的字典集合类。

## <a name="syntax"></a>语法

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|此映射中返回元素的数。|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|确定当前的哈希表中的元素数。|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|获取用于循环的下一个元素。|
|[CMapStringToOb::GetSize](#getsize)|此映射中返回元素的数。|
|[CMapStringToOb::GetStartPosition](#getstartposition)|返回第一个元素的位置。|
|[CMapStringToOb::HashKey](#hashkey)|计算指定的键的哈希值。|
|[CMapStringToOb::InitHashTable](#inithashtable)|初始化哈希表。|
|[CMapStringToOb::IsEmpty](#isempty)|空映射条件 （元素） 的测试。|
|[CMapStringToOb::Lookup](#lookup)|查找的 void 指针关键字的 void 指针。 指针值，而不是它指向的实体用于关键的比较。|
|[CMapStringToOb::LookupKey](#lookupkey)|返回具有指定的密钥值相关联的密钥对的引用。|
|[CMapStringToOb::RemoveAll](#removeall)|此映射中移除所有元素。|
|[CMapStringToOb::RemoveKey](#removekey)|移除由键指定的元素。|
|[CMapStringToOb::SetAt](#setat)|将元素插入到映射;如果找到匹配项，将替换现有元素。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](#operator_at)|将元素插入到映射 — 运算符替换为`SetAt`。|

## <a name="remarks"></a>备注

已插入后`CString` -  `CObject*`对 （元素） 可以有效地检索或删除对使用字符串到映射，或`CString`作为键的值。 此外可以循环访问映射中的所有元素。

位置类型的变量用于备用条目中所有的映射变体的访问权限。 可以使用位置"记住"条目并循环访问映射。 您可能认为此迭代是有顺序的键值;不是这样。 检索元素的序列是不确定。

`CMapStringToOb` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果映射存储到存档，使用重载插入反过来序列的每个元素 ( **<<**) 运算符或`Serialize`成员函数。

如果你需要在映射中的各个元素的诊断转储 (`CString`值和`CObject`内容)，则必须将转储上下文的深度设置为 1 或更高版本。

当`CMapStringToOb`删除对象，或删除它的元素时，`CString`对象和`CObject`删除的指针。 所引用的对象`CObject`指针不会被销毁。

映射类派生是类似于列表派生。 请参阅文章[集合](../../mfc/collections.md)有关的特殊用途的列表类派生的图例。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>要求

**标头：** afxcoll.h

##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb

构造一个空`CString`到`CObject*`映射。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
指定扩展映射的内存分配粒度。

### <a name="remarks"></a>备注

随着映射中的单元分配内存*nBlockSize*条目。

下表显示其他成员函数类似于`CMapStringToOb:: CMapStringToOb`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

##  <a name="getcount"></a>  CMapStringToOb::GetCount

确定在映射中元素的数量。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

此映射中的元素数。

### <a name="remarks"></a>备注

下表显示其他成员函数类似于`CMapStringToOb::GetCount`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize

确定当前的哈希表中的元素数。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>返回值

哈希表中返回元素的数。

### <a name="remarks"></a>备注

下表显示其他成员函数类似于`CMapStringToOb::GetHashTableSize`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc

检索处的地图元素*rNextPosition*，然后更新*rNextPosition*来指代在映射中的下一个元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*rNextPosition*<br/>
指定对先前返回的位置值的引用`GetNextAssoc`或`GetStartPosition`调用。

*rKey*<br/>
指定检索的元素 （字符串） 的返回的密钥。

*rValue*<br/>
指定检索的元素的返回的值 (`CObject`指针)。 有关此参数的详细信息，请参阅备注。

### <a name="remarks"></a>备注

此函数是最适用于通过映射中的所有元素。 请注意，位置序列不一定与密钥值序列相同。

如果检索的元素在映射中上, 一次然后的新值*rNextPosition*设置为 NULL。

有关*rValue*参数，请务必对您对象类型强制转换**CObject\*&**，这是编译器的要求，如下面的示例中所示：

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

这不是 true 的`GetNextAssoc`适用于基于模板的映射。

下表显示其他成员函数类似于`CMapStringToOb::GetNextAssoc`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (位置 & a)** *rNextPosition*  **， void\*&** *rKey* **，WORD 和** *右值* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\*&** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\*&** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\*&** *rValue* **) const;**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程序的结果如下所示：

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>  CMapStringToOb::GetSize

返回地图元素的数。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>返回值

在映射中的项的数目。

### <a name="remarks"></a>备注

调用此方法来检索该映射中的元素数。

下表显示其他成员函数类似于`CMapStringToOb::GetSize`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition

通过返回位置值，可传递给启动映射迭代`GetNextAssoc`调用。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>返回值

位置值，该值指示用于循环访问映射的起始位置或者，如果映射为空，则为 NULL。

### <a name="remarks"></a>备注

迭代序列不是可预测;因此，"映射中的第一个元素"有没有特别的意义。

下表显示其他成员函数类似于`CMapStringToOb::GetStartPosition`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition( ) const;**|

### <a name="example"></a>示例

有关示例，请参阅[CMapStringToOb::GetNextAssoc](#getnextassoc)。

##  <a name="hashkey"></a>  CMapStringToOb::HashKey

计算指定的键的哈希值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>参数

*key*<br/>
将计算其哈希值的键。

### <a name="return-value"></a>返回值

键的哈希值

### <a name="remarks"></a>备注

下表显示其他成员函数类似于`CMapStringToOb::HashKey`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey( WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey( WORD** `key` **) const;**|

##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable

初始化哈希表。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>参数

*hashSize*<br/>
哈希表中的条目数。

*bAllocNow*<br/>
如果为 TRUE，则会分配哈希表初始化; 时否则需要时分配的表。

### <a name="remarks"></a>备注

为了获得最佳性能，哈希表大小应为一个素数。 为了尽量减少冲突，大小应为大约 20%超过最大预期的数据集。

下表显示其他成员函数类似于`CMapStringToOb::InitHashTable`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|

##  <a name="isempty"></a>  CMapStringToOb::IsEmpty

确定是否映射为空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>返回值

此映射不包含任何元素; 如果非零值否则为 0。

### <a name="example"></a>示例

有关示例，请参阅[RemoveAll](#removeall)。

### <a name="remarks"></a>备注

下表显示其他成员函数类似于**CMapStringToOb::IsEmpty**。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

##  <a name="lookup"></a>  CMapStringToOb::Lookup

返回`CObject`上基于指针`CString`值。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要查找的元素的字符串键。

*rValue*<br/>
指定从查找元素的返回的值。

### <a name="return-value"></a>返回值

如果找到该元素; 非零值否则为 0。

### <a name="remarks"></a>备注

`Lookup` 使用哈希算法来快速查找完全匹配的密钥的地图元素 (`CString`值)。

下表显示其他成员函数类似于`CMapStringToOb::LookUp`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, void\*&** `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\*&** `rValue` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **, CObject\*&** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\*&** `rValue` **) const;**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey

返回具有指定的密钥值相关联的密钥对的引用。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于标识要查找的元素的字符串键。

*rKey*<br/>
对关联的键的引用。

### <a name="return-value"></a>返回值

如果找到该键; 非零值否则为 0。

### <a name="remarks"></a>备注

如果使用后关联的元素从映射中删除或映射已被销毁后，使用密钥的引用是不安全。

下表显示其他成员函数类似于`CMapStringToOb:: LookupKey`。

|类|成员函数|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

##  <a name="operator_at"></a>  CMapStringToOb::operator [ ]

便捷替代`SetAt`成员函数。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>返回值

对指向指针的引用`CObject`对象; 或者如果映射为空，则为 NULL 或*密钥*不在范围。

### <a name="remarks"></a>备注

因此它可以仅在左侧和右侧的赋值语句 （左值） 上使用。 如果不存在具有指定键映射元素，则会创建一个新的元素。

没有等效于此运算符的任何"右侧"（右值），因为可能可能映射中找到密钥。 使用`Lookup`元素检索的成员函数。

下表显示其他成员函数类似于`CMapStringToOb::operator []`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& operator\[](void \*</strong> `key` **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD& operator\[](void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator\[](lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString& operator\[](lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 运算符\[] (word** `key`  **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operator\[](word** `key` **\);**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程序的结果如下所示：

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>  CMapStringToOb::RemoveAll

此映射中移除所有元素，并销毁`CString`密钥对象。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

`CObject`所引用的每个键对象不会被销毁。 `RemoveAll`如果您不能确保的引用，函数可能会导致内存泄漏`CObject`对象被销毁。

功能工作正常，如果映射已经为空。

下表显示其他成员函数类似于`CMapStringToOb::RemoveAll`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>  CMapStringToOb::RemoveKey

查找映射条目对应于所提供的密钥;然后，如果找到该键，则移除的项。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>参数

*key*<br/>
指定用于映射查找的字符串。

### <a name="return-value"></a>返回值

如果找到该条目并将其成功移除，则非零值否则为 0。

### <a name="remarks"></a>备注

如果满足以下条件，这可能导致内存泄漏`CObject`对象不会在其他位置删除。

下表显示其他成员函数类似于`CMapStringToOb::RemoveKey`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey( WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey( WORD** `key` **);**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程序的结果如下所示：

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>  CMapStringToOb::SetAt

主要方法要在地图中插入元素。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>参数

*key*<br/>
指定为新元素的键的字符串。

*newValue*<br/>
指定`CObject`是新元素的值的指针。

### <a name="remarks"></a>备注

首先，查找密钥。 如果找到该键，然后更改相应的值;否则将创建一个新的键 / 值元素。

下表显示其他成员函数类似于`CMapStringToOb::SetAt`。

|类|成员函数|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。

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

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 类](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString 类](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb 类](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)
