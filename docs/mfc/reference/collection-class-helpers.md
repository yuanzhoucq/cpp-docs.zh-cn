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
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374813"
---
# <a name="collection-class-helpers"></a>集合类帮助器

集合类`CMap`、`CList`并使用`CArray`模板化全局帮助器函数，用于比较、复制和序列化元素等目的。 作为基于`CMap`的类实现的一部分`CList`，`CArray`必须根据需要使用根据地图、列表或数组中存储的数据类型定制的版本来覆盖这些函数。 有关重写帮助器函数的信息，例如`SerializeElements`，请参阅文章["集合：如何创建类型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)"。 请注意，`ConstructElements`并已`DestructElements`弃用。

Microsoft 基础类库在 afxtempl.h 中提供了以下全局函数，以帮助您自定义集合类：

### <a name="collection-class-helpers"></a>集合类帮助器

|||
|-|-|
|[CompareElements](#compareelements)|指示元素是否相同。|
|[CopyElements](#copyelements)|将元素从一个数组复制到另一个数组。|
|[DumpElements](#dumpelements)|提供面向流的诊断输出。|
|[哈希基](#hashkey)|计算哈希键。|
|[SerializeElements](#serializeelements)|将元素存储或检索到存档或从存档中检索。|

## <a name="compareelements"></a><a name="compareelements"></a>比较元素

直接调用 [CList：：Find]（clist-class.md.not_found.md_clist__find，由[cmap__lookup](cmap-class.md#lookup)和[cmap__operator &#91;&#93;](cmap-class.md#operator_at)间接调用。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>参数

*类型*<br/>
要比较的第一个元素的类型。

*p元素1*<br/>
指向要比较的第一个元素的指针。

*ARG_TYPE*<br/>
要比较的第二个元素的类型。

*p元素2*<br/>
指向要比较的第二个元素的指针。

### <a name="return-value"></a>返回值

如果*pElement1*指向的对象等于*pElement2*指向的对象，则非零;否则 0。

### <a name="remarks"></a>备注

调用`CMap`使用`CMap`模板参数*KEY*和*ARG_KEY*。

默认实现返回*\*pElement1*和*\*pElement2*的比较结果。 重写此函数，以便以适合应用程序的方式比较元素。

C++语言为简单类型（**字符****、int、float**等）定义比较运算符**float**（），`==`但不定义类和结构的比较运算符。 如果要使用`CompareElements`或实例化使用它的集合类之一，则必须定义比较运算符或使用返回适当值的版本重载`CompareElements`。

### <a name="requirements"></a>要求

   **标头：** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>复制元素

此函数由[CArray：：追加和](carray-class.md#append) [CArray：：copy](carray-class.md#copy)直接调用。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定要复制的元素类型的模板参数。

*pDest*<br/>
指向将复制元素的目标位置。

*pSrc*<br/>
指向要复制的元素的源。

*nCount*<br/>
要复制的元素的数量。

### <a name="remarks"></a>备注

默认实现使用简单赋值运算符 （ **=** ） 执行复制操作。 如果复制类型没有重载操作符 =，则默认实现将执行按位复制。

有关实现此函数和其他帮助器函数的信息，请参阅文章["集合：如何创建类型安全集合](../how-to-make-a-type-safe-collection.md)"。

### <a name="requirements"></a>要求

  **头**afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>转储元素

在重写时，以文本形式为集合元素提供面向流的诊断输出。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>参数

*直流*<br/>
转储元素的转储上下文。

*类型*<br/>
指定元素类型的模板参数。

*p元素*<br/>
指向要转储的元素的指针。

*nCount*<br/>
要转储的元素数。

### <a name="remarks"></a>备注

如果转储的深度大于`CMap::Dump`0，则`CArray::Dump`调用 和 函数将调用此。 `CList::Dump`

默认实现不执行任何操作。 如果集合的元素派生自`CObject`，则重写通常会遍转集合的元素，依次调用`Dump`每个元素。

### <a name="requirements"></a>要求

  **头**afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>哈希基

计算给定键的哈希值。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>参数

*ARG_KEY*<br/>
指定用于访问映射键的数据类型的模板参数。

*关键*<br/>
要计算哈希值的键。

### <a name="return-value"></a>返回值

键的哈希值。

### <a name="remarks"></a>备注

此函数由[CMap 直接调用：：删除Key，](cmap-class.md#removekey)并间接由[CMap：：查找](cmap-class.md#lookup)和[CMap：：：运算符 &#91;&#93;](cmap-class.md#operator_at)。

默认实现通过将*键*向右移动四个位置来创建哈希值。 重写此函数，以便返回适合应用程序的哈希值。

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

  **头**afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>序列化元素

[CArray、CList](carray-class.md)和[CMap](cmap-class.md)调用此函数来序列化元素。 [CList](clist-class.md)

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>参数

*类型*<br/>
指定元素类型的模板参数。

*ar*<br/>
要存档到或从存档的存档对象。

*p元素*<br/>
指向要存档的元素的指针。

*nCount*<br/>
要存档的元素数

### <a name="remarks"></a>备注

默认实现执行位读取或写入。

有关实现此函数和其他帮助器函数的信息，请参阅文章["集合：如何创建类型安全集合](../how-to-make-a-type-safe-collection.md)"。

### <a name="example"></a>示例

请参阅文章["集合：如何创建类型安全集合"中](../how-to-make-a-type-safe-collection.md)的示例。

### <a name="requirements"></a>要求

  **头**afxtempl.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CMap 类](cmap-class.md)<br/>
[CList 类](clist-class.md)<br/>
[CArray 类](carray-class.md)
