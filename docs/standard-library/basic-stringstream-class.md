---
title: "basic_stringstream 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6616f5eadc5291b917d7121f5eebb92baeec8c3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="basicstringstream-class"></a>basic_stringstream 类
描述了一个对象，该对象可通过使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区控制元素和编码对象的插入和提取。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>参数  
 `Alloc`  
 allocator 类。  
  
 `Elem`  
 字符串的基本元素的类型。  
  
 *Tr*  
 字符串的基本元素上专用的字符特征。  
  
## <a name="remarks"></a>备注  
 该模板类描述了一个对象，该对象可通过使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区控制元素和编码对象的插入和提取，其中 **Elem** 类型的元素的字符特征由类 **Tr** 确定，且其元素由类 `Alloc` 的分配器进行分配。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[basic_stringstream](#basic_stringstream)|构造 `basic_stringstream` 类型的对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|该类型是模板参数 `Alloc`的同义词。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|向 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> 返回 `pointer` 类型的已存储流缓冲区的地址。|  
|[str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<sstream>  
  
 **命名空间：** std  
  
##  <a name="allocator_type"></a>  basic_stringstream::allocator_type  
 该类型是模板参数 `Alloc` 的同义词。  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream  
 构造 `basic_stringstream` 类型的对象。  
  
```  
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>参数  
 `_Mode`  
 [ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。  
  
 `str`  
 一个 `basic_string` 类型的对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过调用 [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**) 来初始化基类，其中 **sb** 是类 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 的存储对象。 通过调用 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode`)，它还可以初始化 **sb**。  
  
 第二个构造函数通过调用 basic_iostream( **sb**) 初始化基类。 通过调用 basic_stringbuf< **Elem**, **Tr**, `Alloc`>(_ *Str*, `_Mode`)，它还可以初始化 **sb**。  
  
##  <a name="rdbuf"></a>  basic_stringstream::rdbuf  
 将**指针**类型的已存储流缓冲区的地址返回到 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>返回值  
 返回到 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 的**指针**类型的已存储流缓冲区的地址。  
  
### <a name="example"></a>示例  
  有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。  
  
##  <a name="str"></a>  basic_stringstream::str  
 设置或获取字符串缓冲区中的文本，而无需更改写入位置。  
  
```  
basic_string<Elem, Tr, Alloc> str() const;

 
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```  
  
### <a name="parameters"></a>参数  
 `_Newstr`  
 新字符串。  
  
### <a name="return-value"></a>返回值  
 返回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 类的对象，它的受控序列是 **\*this** 控制的序列副本。  
  
### <a name="remarks"></a>备注  
 第一个成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二个成员函数调用 `rdbuf` -> **str**( `_Newstr`)。  
  
### <a name="example"></a>示例  
  请参阅 [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str)，了解使用 **str** 的示例。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)

