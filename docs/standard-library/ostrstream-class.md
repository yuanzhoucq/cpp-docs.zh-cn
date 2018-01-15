---
title: "ostrstream 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs: C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33dfff06bdc9cd9005cb2fe8e04a3f8447cf1edc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ostrstream-class"></a>ostrstream 类
描述控制元素插入的对象，并将对象编码到 [strstreambuf](../standard-library/strstreambuf-class.md) 类的流缓冲区中。  
  
## <a name="syntax"></a>语法  
  
```
class ostrstream : public ostream
```  
  
## <a name="remarks"></a>备注  
 该对象存储 `strstreambuf` 类的对象。  
  
> [!NOTE]
>  此类已弃用。 请考虑使用 [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) 或 [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) 作为替代。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[ostrstream](#ostrstream)|构造 `ostrstream` 类型的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[freeze](#freeze)|导致无法通过流缓冲区操作使用流缓冲区。|  
|[pcount](#pcount)|返回写入到受控序列的元素计数。|  
|[rdbuf](#rdbuf)|返回指向流的关联 `strstreambuf` 对象的指针。|  
|[str](#str)|调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<strstream>  
  
 **命名空间：** std  
  
##  <a name="freeze"></a>  ostrstream::freeze  
 导致无法通过流缓冲区操作使用流缓冲区。  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>参数  
 `_Freezeit`  
 `bool` 指示是否要冻结流。  
  
### <a name="remarks"></a>备注  
 此成员函数调用 [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*)。  
  
### <a name="example"></a>示例  
  有关使用 **freeze** 的示例，请参阅 [strstream::freeze](../standard-library/strstreambuf-class.md#freeze)。  
  
##  <a name="ostrstream"></a>  ostrstream::ostrstream  
 构造 `ostrstream` 类型的对象。  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 缓冲区。  
  
 `count`  
 缓冲区的大小（以字节为单位）。  
  
 `_Mode`  
 缓冲区的输入和输出模式。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。  
  
### <a name="remarks"></a>备注  
 这两个构造函数均可通过调用 [ostream](../standard-library/ostream-typedefs.md#ostream)( **sb**)（其中 **sb** 是 [strstreambuf](../standard-library/strstreambuf-class.md) 类的存储的对象）初始化基类。 第一个构造函数还可通过调用 `strstreambuf` 初始化 **sb**。 第二个构造函数以下列两种方式之一初始化基类：  
  
-   如果 `_Mode` & **ios_base::app**== 0，则 `ptr` 必须指定 `count` 元素数组的第一个元素，且构造函数调用 `strstreambuf`( `ptr`, `count`, `ptr`)。  
  
-   否则，`ptr` 必须指定包含 C 字符串（其第一个元素由 `ptr` 指定）的计数元素数组的第一个元素，且构造函数调用 `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) )。  
  
##  <a name="pcount"></a>  ostrstream::pcount  
 返回写入到受控序列的元素计数。  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>返回值  
 写入到受控序列的元素数。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
### <a name="example"></a>示例  
  有关使用 `pcount` 的示例，请参阅 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="rdbuf"></a>  ostrstream::rdbuf  
 返回指向流关联的 strstreambuf 对象的指针。  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>返回值  
 指向流关联的 strstreambuf 对象的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数将**指针**类型的已存储流缓冲区的地址返回到 [strstreambuf](../standard-library/strstreambuf-class.md)。  
  
### <a name="example"></a>示例  
  有关使用 `rdbuf` 的示例，请参阅 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。  
  
##  <a name="str"></a>  ostrstream::str  
 调用 [freeze](../standard-library/strstreambuf-class.md#freeze)，然后将返回指向受控序列开头的指针。  
  
```
char *str();
```  
  
### <a name="return-value"></a>返回值  
 指向受控序列的开头的指针。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。  
  
### <a name="example"></a>示例  
  有关使用 **str** 的示例，请参阅 [strstream::str](../standard-library/strstreambuf-class.md#str)。  
  
## <a name="see-also"></a>请参阅  
 [ostream](../standard-library/ostream-typedefs.md#ostream)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



