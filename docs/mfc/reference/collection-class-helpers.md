---
title: 集合类帮助器
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 02bc5c5a7c1766c97d9a834c8b6b4dfb2a26ae82
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231788"
---
# <a name="collection-class-helpers"></a>集合类帮助器

集合类 `CMap` 、 `CList` 和 `CArray` 使用模板化全局 helper 函数，以便对元素进行比较、复制和序列化。 作为基于、和的类实现的一部分 `CMap` `CList` `CArray` ，你必须根据需要重写这些函数，使其适合你的映射、列表或数组中所存储的数据类型。 有关重写 helper 函数（如）的信息 `SerializeElements` ，请参阅文章[集合：如何进行类型安全的集合](../../mfc/how-to-make-a-type-safe-collection.md)。 请注意， `ConstructElements` 和已 `DestructElements` 被弃用。

Microsoft 基础类库在 afxtempl.h 中提供了以下全局函数，以帮助你自定义集合类：

### <a name="collection-class-helpers"></a>集合类帮助器

|||
|-|-|
|[CompareElements](#compareelements)|指示元素是否相同。|
|[CopyElements](#copyelements)|将元素从一个数组复制到另一个数组。|
|[DumpElements](#dumpelements)|提供面向流的诊断输出。|
|[HashKey](#hashkey)|计算哈希键。|
|[SerializeElements](#serializeelements)|在存档中存储或检索元素。|

## <a name="compareelements"></a><a name="compareelements"></a>CompareElements

直接由 [CList：： Find] （CList # clist__find not_found [cmap__lookup](cmap-class.md#lookup)和[cmap__operator &#91;&#93;](cmap-class.md#operator_at)直接调用。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>参数

*TYPE*<br/>
要比较的第一个元素的类型。

*pElement1*<br/>
指向要比较的第一个元素的指针。

*ARG_TYPE*<br/>
要比较的第二个元素的类型。

*pElement2*<br/>
指向要比较的第二个元素的指针。

### <a name="return-value"></a>返回值

如果*pElement1*指向的对象等于*pElement2*指向的对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

`CMap`调用使用 `CMap` 模板参数*密钥*并*ARG_KEY*。

默认实现返回* \* pElement1*和* \* pElement2*的比较结果。 重写此函数，使其以适用于你的应用程序的方式对元素进行比较。

C + + 语言 `==` 为简单类型（、、等）定义比较运算符（）， **`char`** **`int`** **`float`** 但未定义类和结构的比较运算符。 如果要使用 `CompareElements` 或来实例化使用它的一个集合类，则必须 `CompareElements` 使用返回适当值的版本定义比较运算符或重载。

### <a name="requirements"></a>要求

   **标头：** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

通过[CArray：： Append](carray-class.md#append)和[CArray：： Copy](carray-class.md#copy)直接调用此函数。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定要复制的元素类型的模板参数。

*pDest*<br/>
指向将复制元素的目标位置。

*.Psrc*<br/>
指向要复制的元素的源。

*nCount*<br/>
要复制的元素的数量。

### <a name="remarks"></a>备注

默认实现使用简单赋值运算符（ **=** ）来执行复制操作。 如果复制类型没有重载操作符 =，则默认实现将执行按位复制。

有关实现此和其他帮助器函数的信息，请参阅文章[集合：如何进行类型安全的集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>要求

  **标头**afxtempl。h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements

重写时，为集合的元素提供面向流的诊断输出（以文本形式提供）。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>参数

*台*<br/>
转储元素的转储上下文。

*TYPE*<br/>
指定元素类型的模板参数。

*pElements*<br/>
指向要转储的元素的指针。

*nCount*<br/>
要转储的元素数。

### <a name="remarks"></a>备注

`CArray::Dump` `CList::Dump` `CMap::Dump` 如果转储的深度大于0，则、和函数将调用此。

默认实现不执行任何操作。 如果集合的元素派生自 `CObject` ，则重写通常会循环访问集合的元素， `Dump` 进而依次调用每个元素。

### <a name="requirements"></a>要求

  **标头**afxtempl。h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey

计算给定键的哈希值。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>参数

*ARG_KEY*<br/>
指定用于访问映射键的数据类型的模板参数。

*key*<br/>
要计算其哈希值的键。

### <a name="return-value"></a>返回值

键的哈希值。

### <a name="remarks"></a>备注

此函数直接由[CMap：： RemoveKey](cmap-class.md#removekey)和[CMap：： Lookup](cmap-class.md#lookup)和[CMap：： Operator &#91;&#93;](cmap-class.md#operator_at)调用。

默认实现通过将*键*向右移位四个位置来创建一个哈希值。 重写此函数，使其返回适用于你的应用程序的哈希值。

### <a name="example"></a>示例

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>要求

  **标头**afxtempl。h

## <a name="serializeelements"></a><a name="serializeelements"></a>SerializeElements

[CArray](carray-class.md)、 [CList](clist-class.md)和[CMap](cmap-class.md)调用此函数以序列化元素。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>参数

*TYPE*<br/>
指定元素类型的模板参数。

*ar*<br/>
要存档到或的存档对象。

*pElements*<br/>
指向要存档的元素的指针。

*nCount*<br/>
正在存档的元素数

### <a name="remarks"></a>备注

默认实现执行按位 "读取" 或 "写入"。

有关实现此和其他帮助器函数的信息，请参阅文章[集合：如何进行类型安全的集合](../how-to-make-a-type-safe-collection.md)。

### <a name="example"></a>示例

请参阅文章集合中的示例[：如何进行类型安全的集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>要求

  **标头**afxtempl。h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CMap 类](cmap-class.md)<br/>
[CList 类](clist-class.md)<br/>
[CArray 类](carray-class.md)
