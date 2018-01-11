---
title: "Vector:: 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
dev_langs: C++
helpviewer_keywords: Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c371b6805616ff0b114be24bb291469eae2dd26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 类
表示可按照索引单独访问的对象的有序集合。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename T, typename E>  
   ref class Vector sealed;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 向量对象中包含的元素的类型。  
  
 `E`  
 使用 `T` 类型的值指定测试相等性的二进制谓词。 默认值为 `std::equal_to<T>`。  
  
### <a name="remarks"></a>备注  
 允许的类型包括：  
  
1.  整数  
  
2.  接口类 ^  
  
3.  公共 ref 类  
  
4.  value struct  
  
5.  公共枚举类  
  
 Vector 类是 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 接口的 C++ 具体实现。  
  
 如果您尝试在公共返回值或参数中使用 Vector 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410)可修复该错误。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Vector:: vector](#ctor)|初始化 Vector 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Vector:: append](#append)|在当前向量中的最后一项后插入指定项。|  
|[Vector:: clear](#clear)|删除当前向量中的所有元素。|  
|[Vector:: first](#first)|返回指定该向量中第一个元素的迭代器。|  
|[Vector:: getat](#getat)|检索由指定索引标识的当前向量的元素。|  
|[Vector:: getmany](#getmany)|从指定索引处开始，检索当前向量中的项目序列。|  
|[Vector:: getview](#getview)|返回向量的只读视图，即 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|  
|[Vector:: indexof](#indexof)|在当前向量中搜索指定项，如果找到，则返回该项的索引。|  
|[Vector:: insertat](#insertat)|在当前 Vector 中由指定的索引标识的元素后面插入指定的项。|  
|[Vector:: replaceall](#replaceall)|删除当前向量中的元素，然后插入来自指定数组的元素。|  
|[Vector:: removeat](#removeat)|从当前向量删除指定索引标识的元素。|  
|[Vector:: removeatend](#removeatend)|删除当前矢量末尾的元素。|  
|[Vector:: setat](#setat)|将指定值分配给当前向量中指定索引标识的元素。|  
|[Vector:: size](#size)|返回当前向量对象中的元素数目。|  
  
### <a name="events"></a>事件  
  
|||  
|-|-|  
|name|描述|  
|事件[Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|当向量更改时发生。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Vector`  
  
### <a name="requirements"></a>惠?  
 **标头：** collection.h  
  
 **命名空间：** Platform::Collections  

## <a name="append"></a>Vector:: append 方法
在当前向量中的最后一项后插入指定项。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void Append(T item);  
```  
  
### <a name="parameters"></a>参数  
 `index`  
 要插入到向量中的项。 一种`item`由定义*T*类型名称。  
  


## <a name="clear"></a>Vector:: clear 方法
删除当前向量中的所有元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void Clear();  
```   


## <a name="first"></a>Vector:: first 方法
返回指向该向量中第一个元素的迭代器。  
  
### <a name="syntax"></a>语法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator <T>^ First();  
```  
  
### <a name="return-value"></a>返回值  
 指向该向量中第一个元素的迭代器。  
  
### <a name="remarks"></a>备注  
 保留 first 返回的迭代器一种简便方式是将返回值分配给使用声明的变量**自动**类型推导关键字。 例如 `auto x = myVector->First();`。 此迭代器知道该集合的长度。  
  
 当你需要一对要传递到 STL 函数的迭代器时，使用自由格式函数[Windows::Foundation::Collections:: 开始](../cppcx/begin-function.md)和[Windows::Foundation::Collections::end](../cppcx/end-function.md)  
  


## <a name="getat"></a>Vector:: getat 方法
检索由指定索引标识的当前向量的元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual T GetAt(unsigned int index);  
```  
  
### <a name="parameters"></a>参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  
### <a name="return-value"></a>返回值  
 `index` 参数指定的元素。 元素类型由*T*类型名称。  
  


## <a name="getmany"></a>Vector:: getmany 方法
检索当前向量中的项序列，从指定的索引开始，并将它们复制到调用方分配的数组中。  
  
### <a name="syntax"></a>语法  
  
```    
virtual unsigned int GetMany(
    unsigned int startIndex, 
    Platform::WriteOnlyArray<T>^ dest);  
```  
  
### <a name="parameters"></a>参数  
 `startIndex`  
 要检索的项开头从零开始的索引。  
  
 `dest`  
 调用方分配的项数组，以由 `startIndex` 指定的元素开始，以向量中最后一个元素结尾。  
  
### <a name="return-value"></a>返回值  
 已检索的项的数量。  
  
### <a name="remarks"></a>备注  
 此函数并非旨在由客户端代码直接使用。 在内部使用它[to_vector Function](../cppcx/to-vector-function.md)若要启用的 platform 实例到 std:: vector 实例的高效转换。  
  


## <a name="getview"></a>Vector:: getview 方法
返回向量的只读视图，即 IVectorView。  
  
### <a name="syntax"></a>语法  
  
```    
Windows::Foundation::Collections::IVectorView<T>^ GetView();  
```  
  
### <a name="return-value"></a>返回值  
 一个 IVectorView 对象。  
  


## <a name="indexof"></a>Vector:: indexof 方法
在当前向量中搜索指定项，如果找到，则返回该项的索引。  
  
### <a name="syntax"></a>语法  
  
```  
  
virtual bool IndexOf(T value, unsigned int* index);  
```  
  
### <a name="parameters"></a>参数  
 `value`  
 要查找的项。  
  
 `index`  
 如果找到参数 `value`，则为该项的从零开始的索引；否则，为 0。  
  
 如果该项目是 Vector 的第一个元素，或者未找到该项目，则 `index` 参数为 0。 如果返回值为 `true`，则表明找到该项目，并且它是第一个元素；否则，表示未找到该项目。  
  
### <a name="return-value"></a>返回值  
 如果找到指定项目，则为 `true`；否则，为 `false`。  
  
### <a name="remarks"></a>备注  
 IndexOf 使用 std::find_if 查找该项目。 因此，自定义元素类型应该重载 == 和 != 运算符以支持 find_if 所需的相等性比较。  
  


##  <a name="insertat"></a>Vector:: insertat 方法
在当前 Vector 中由指定的索引标识的元素后面插入指定的项。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void InsertAt(unsigned int index, T item)  
```  
  
### <a name="parameters"></a>参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  
 `item`  
 要插入到 Vector 中由 `index` 指定的元素后面的项。 一种`item`由定义*T*类型名称。  
  


## <a name="removeat"></a>Vector:: removeat 方法
从当前向量删除指定索引标识的元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void RemoveAt(unsigned int index);  
```  
  
### <a name="parameters"></a>参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  


## <a name="removeatend"></a>Vector:: removeatend 方法
删除当前矢量末尾的元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void RemoveAtEnd();  
```  
  


## <a name="replaceall"></a>Vector:: replaceall 方法
删除当前向量中的元素，然后插入来自指定数组的元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);  
```  
  
### <a name="parameters"></a>参数  
 `arr`  
 其类型定义的对象的数组*T*类型名称。  
  


## <a name="setat"></a>Vector:: setat 方法
将指定值分配给当前向量中指定索引标识的元素。  
  
### <a name="syntax"></a>语法  
  
```    
virtual void SetAt(unsigned int index, T item);  
```  
  
### <a name="parameters"></a>参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  
 `item`  
 要分配给指定元素的值。 一种`item`由定义*T*类型名称。  
  


## <a name="size"></a>Vector:: size 方法
返回当前向量对象中的元素数目。  
  
### <a name="syntax"></a>语法  
  
```    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>返回值  
 当前 Vector 中的元素数目。  
  


## <a name="ctor"></a>Vector:: vector 构造函数
初始化 Vector 类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
Vector();  
  
explicit Vector(unsigned int size);  
Vector( unsigned int size, T value);    
template <typename U> explicit Vector( const ::std::vector<U>& v);    
template <typename U> explicit Vector( std::vector<U>&& v);    

Vector( const T * ptr, unsigned int size);    
template <size_t N> explicit Vector(const T(&arr)[N]);    
template <size_t N> explicit Vector(const std::array<T, N>& a);   
explicit Vector(const Array<T>^ arr);  
  
template <typename InIt> Vector(InIt first, InIt last);   
Vector(std::initializer_list<T> il);  
```  
  
### <a name="parameters"></a>参数  
 a  
 A [std:: array](../standard-library/array-class-stl.md)将用于初始化向量。  
  
 a  
 A [platform:: array](../cppcx/platform-array-class.md)将用于初始化向量。  
  
 `InIt`  
 用于初始化当前向量的对象集合的类型。  
  
 il  
 A [std:: initializer_list](../standard-library/initializer-list-class.md)类型的对象的`T`将用于初始化向量。  
  
 `N`  
 用于初始化当前向量的对象集合中的元素数。  
  
 `size`  
 向量中元素的数目。  
  
 `value`  
 用于初始化当前向量中每个元素的值。  
  
 `v`  
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std:: vector](../standard-library/vector-class.md)用于初始化当前向量。  
  
 `ptr`  
 指向用于初始化当前向量的 `std::vector` 的指针。  
  
 `arr`  
 A [platform:: array](../cppcx/platform-array-class.md)用于初始化当前向量的对象。  
  
 `a`  
 A [std:: array](../standard-library/array-class-stl.md)用于初始化当前向量的对象。  
  
 `first`  
 用于初始化当前向量的对象序列中的第一个元素。 一种`first`通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 `last`  
 用于初始化当前向量的对象序列中的最后一个元素。 一种`last`通过传递*完美转发*。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  


  
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)   
 [C + + 创建 Windows 运行时组件](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)