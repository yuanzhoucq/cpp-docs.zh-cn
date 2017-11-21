---
title: "CMapStringToOb 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e5ffa1822a983e3792e1484b612ee11288dd547
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
|[CMapStringToOb::GetCount](#getcount)|在此地图中返回元素的数。|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|确定当前的哈希表中的元素数。|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|获取循环的下一个元素。|  
|[CMapStringToOb::GetSize](#getsize)|在此地图中返回元素的数。|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|返回的第一个元素的位置。|  
|[CMapStringToOb::HashKey](#hashkey)|计算指定的键的哈希值。|  
|[CMapStringToOb::InitHashTable](#inithashtable)|初始化哈希表。|  
|[CMapStringToOb::IsEmpty](#isempty)|空映射条件 （没有元素） 的测试。|  
|[CMapStringToOb::Lookup](#lookup)|查找基于 void 指针密钥的 void 指针。 指针值，它指向不实体用于键的比较。|  
|[CMapStringToOb::LookupKey](#lookupkey)|返回与指定的密钥值关联的密钥的引用。|  
|[CMapStringToOb::RemoveAll](#removeall)|从此映射中移除所有元素。|  
|[CMapStringToOb::RemoveKey](#removekey)|移除由键指定的元素。|  
|[CMapStringToOb::SetAt](#setat)|将元素插入到映射;如果找到匹配的键，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::operator]](#operator_at)|将元素插入到映射 — 运算符替换`SetAt`。|  
  
## <a name="remarks"></a>备注  
 一旦已插入`CString` -  `CObject*`对 （元素） 到映射中，你可以高效地检索或删除对使用字符串或`CString`作为键的值。 此外可以循环访问映射中的所有元素。  
  
 类型的变量的**位置**适用于所有地图变体中的备用条目访问。 你可以使用**位置**"记住"条目和循环通过映射。 你可能会认为此迭代是根据键值; 顺序不存在。 检索元素的序列是不确定的。  
  
 `CMapStringToOb` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果映射存储到存档中，使用重载插入反过来序列的每个元素 (  **<<** ) 运算符或`Serialize`成员函数。  
  
 如果你需要在映射中的各个元素的诊断转储 (`CString`值和`CObject`内容)，必须将转储上下文的深度设置为 1 或更高版本。  
  
 当`CMapStringToOb`对象被删除，或删除其元素时，`CString`对象和`CObject`删除的指针。 引用的对象`CObject`指针不会被销毁。  
  
 映射类派生是类似于列表派生。 请参阅文章[集合](../../mfc/collections.md)有关特殊用途列表类派生的图例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb  
 构造一个空`CString`到`CObject*`映射。  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 指定扩展映射的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 随着映射后，内存分配的单位`nBlockSize`条目。  
  
 下表显示其他成员函数类似于**CMapStringToOb:: CMapStringToOb**。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
##  <a name="getcount"></a>CMapStringToOb::GetCount  
 确定在映射中元素数量。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 此映射中的元素数目。  
  
### <a name="remarks"></a>备注  
 下表显示其他成员函数类似于`CMapStringToOb::GetCount`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize  
 确定当前的哈希表中的元素数。  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回哈希表中的元素数。  
  
### <a name="remarks"></a>备注  
 下表显示其他成员函数类似于`CMapStringToOb::GetHashTableSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize （) const;**|  
  
##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc  
 检索处的地图元素*rNextPosition*，然后更新*rNextPosition*来引用映射中的下一个元素。  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 *rNextPosition*  
 指定对引用**位置**通过前一个返回值**GetNextAssoc**或**GetStartPosition**调用。  
  
 *rKey*  
 指定检索的元素 （字符串） 的返回的密钥。  
  
 *右值*  
 指定检索的元素的返回的值 ( **CObject**指针)。 有关此参数的详细信息，请参阅备注。  
  
### <a name="remarks"></a>备注  
 此函数是最适用于循环访问映射中的所有元素。 请注意，位置序列不一定是相同的密钥值序列。  
  
 如果检索的元素的是在映射中，最后然后的新值*rNextPosition*设置为**NULL**。  
  
 有关*右值*参数，请务必类型强制转换你对象为**CObject\*&**，这是编译器的要求，如下面的示例中所示：  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 这是不正确的**GetNextAssoc**适用于基于模板的映射。  
  
 下表显示其他成员函数类似于**CMapStringToOb::GetNextAssoc**。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，void\* &**  *rKey* **，void\*&**  *右值* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，void\* &**  *rKey* **，WORD 和***右值* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，CString &** *rKey* **，void\* &** *右值* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，CString &** *rKey* **，CString &** *右值* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，WORD （& a)** *rKey* **，CObject\* &** *右值* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (位置 （& a)** *rNextPosition* **，WORD （& a)** *rKey* **，void\* &** *右值* **) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 此程序的结果如下所示：  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>CMapStringToOb::GetSize  
 返回地图元素的数。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 在映射中的项的数目。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索在映射中的元素的数目。  
  
 下表显示其他成员函数类似于`CMapStringToOb::GetSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize （) const;**|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition  
 通过返回启动映射迭代**位置**值，可以传递给`GetNextAssoc`调用。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**值，该值指示来循环映射; 的起始位置或**NULL**如果映射为空。  
  
### <a name="remarks"></a>备注  
 迭代序列是不可预测的;因此，"映射中的第一个元素"必须没有特别的意义。  
  
 下表显示其他成员函数类似于`CMapStringToOb::GetStartPosition`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**位置 GetStartPosition （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**位置 GetStartPosition （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**位置 GetStartPosition （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**位置 GetStartPosition （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**位置 GetStartPosition （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**位置 GetStartPosition （) const;**|  
  
### <a name="example"></a>示例  
 请参阅示例[CMapStringToOb::GetNextAssoc](#getnextassoc)。  
  
##  <a name="hashkey"></a>CMapStringToOb::HashKey  
 计算指定的键的哈希值。  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 键，其哈希值是要从中计算。  
  
### <a name="return-value"></a>返回值  
 键的哈希值  
  
### <a name="remarks"></a>备注  
 下表显示其他成员函数类似于`CMapStringToOb::HashKey`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void\***  `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const;**|  
  
##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable  
 初始化哈希表。  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `hashSize`  
 哈希表中的条目数。  
  
 `bAllocNow`  
 如果**TRUE**，分配哈希表初始化; 在需要时否则分配表。  
  
### <a name="remarks"></a>备注  
 为了获得最佳性能，哈希表大小应为质数。 为了尽量减少冲突，则大小应为大致大于最大预期的数据集的 20%。  
  
 下表显示其他成员函数类似于`CMapStringToOb::InitHashTable`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>CMapStringToOb::IsEmpty  
 确定是否映射为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此映射不包含任何元素; 则为非 0否则为 0。  
  
### <a name="example"></a>示例  
 请参阅示例[RemoveAll](#removeall)。  
  
### <a name="remarks"></a>备注  
 下表显示其他成员函数类似于**CMapStringToOb:: IsEmpty**。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty （) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty （) const;**|  
  
##  <a name="lookup"></a>CMapStringToOb::Lookup  
 返回`CObject`指针基于`CString`值。  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定标识要查找的元素的字符串键。  
  
 `rValue`  
 指定查阅到元素中的返回的值。  
  
### <a name="return-value"></a>返回值  
 如果该元素; 如果未找到则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lookup`使用哈希算法来快速查找完全匹配的密钥的地图元素 (`CString`值)。  
  
 下表显示其他成员函数类似于`CMapStringToOb::LookUp`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 查找 (void\***  `key` **，void\* &**  `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 查找 (void\***  `key` **，WORD （& a)** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找 (LPCTSTR** `key` **，void\* &**  `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找 (LPCTSTR** `key` **，CString &** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 查找 (WORD** `key` **，CObject\* &**  `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 查找 (WORD** `key` **，void\* &**  `rValue` **) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>CMapStringToOb::LookupKey  
 返回与指定的密钥值关联的密钥的引用。  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定标识要查找的元素的字符串键。  
  
 `rKey`  
 对关联的键的引用。  
  
### <a name="return-value"></a>返回值  
 如果找到该键，; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果使用后，关联的元素已从映射中移除或映射已被销毁后，使用对密钥的引用是不安全的。  
  
 下表显示其他成员函数类似于**CMapStringToOb:: LookupKey**。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR （& a)** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR （& a)** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>CMapStringToOb::operator]  
 一个方便替换`SetAt`成员函数。  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>返回值  
 对指向的指针的引用`CObject`对象; 或**NULL**如果映射为空或`key`超出范围。  
  
### <a name="remarks"></a>备注  
 因此它可以仅在赋值语句 （左值） 的左侧使用。 如果没有地图元素与指定的键，则会创建一个新的元素。  
  
 没有等效于此运算符的任何"右侧"（右值），因为一个密钥可能无法找到在映射中的可能。 使用`Lookup`元素检索的成员函数。  
  
 下表显示其他成员函数类似于**CMapStringToOb::operator []**。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& 运算符 [] (void\***  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD （&) 运算符 [] (void\***  `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& 运算符 [] (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & 运算符 [] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 运算符 [] (word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& 运算符 [] (word** `key`  **\);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 此程序的结果如下所示：  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>CMapStringToOb::RemoveAll  
 从该映射中移除所有元素和销毁`CString`密钥对象。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 `CObject`所引用的每个键对象不会被销毁。 `RemoveAll`函数可以导致内存泄漏，如果您不能确保该引用`CObject`对象被销毁。  
  
 如果映射已经为空，该函数能正常工作。  
  
 下表显示其他成员函数类似于`CMapStringToOb::RemoveAll`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll （);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll （);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll （);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll （);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll （);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>CMapStringToOb::RemoveKey  
 查找与提供的键; 相对应的映射条目然后，如果找到该键中, 移除的项。  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定用于映射查找的字符串。  
  
### <a name="return-value"></a>返回值  
 如果该条目已成功找到并移除; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 这会导致内存泄漏，如果`CObject`不其他地方删除对象。  
  
 下表显示其他成员函数类似于`CMapStringToOb::RemoveKey`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 此程序的结果如下所示：  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>CMapStringToOb::SetAt  
 主要方法将一个元素插入映射中。  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指定为新元素的键的字符串。  
  
 `newValue`  
 指定`CObject`是新的元素的值的指针。  
  
### <a name="remarks"></a>备注  
 首先，查找键。 如果找到该键，则相应的值发生更改;否则，将创建一个新的键值对的元素。  
  
 下表显示其他成员函数类似于`CMapStringToOb::SetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void\***  `key` **，void\***  `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void\***  `key` **，WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **，void\***  `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **，LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **，CObject\***  `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **，void\***  `newValue` **);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`所有集合示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 此程序的结果如下所示：  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr 类](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord 类](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr 类](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString 类](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb 类](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr 类](../../mfc/reference/cmapwordtoptr-class.md)
