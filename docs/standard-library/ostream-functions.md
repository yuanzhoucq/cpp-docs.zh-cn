---
title: "&lt;ostream&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 15
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 89eebd013c08f52175e5e4038b501d4ce572e55a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函数
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ends](#ends)|  
|[flush](#flush)|  
  
##  <a name="endl"></a>endl  
 终止行并刷新缓冲区。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& endl(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>参数  
 `Elem`  
 元素类型。  
  
 `Ostr`  
 一个 `basic_ostream` 类型的对象。  
  
 `Tr`  
 字符特征。  
  
### <a name="return-value"></a>返回值  
 一个 `basic_ostream` 类型的对象。  
  
### <a name="remarks"></a>备注  
 该操控器调用 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Ostr`**.** [widen](../standard-library/basic-ios-class.md#widen)( **'\n'**))，然后调用 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush)。 它将返回 `Ostr`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostream_endl.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << endl;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="ends"></a>  ends  
 终止字符串。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& ends(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>参数  
 `Elem`  
 元素类型。  
  
 `Ostr`  
 一个 `basic_ostream` 类型的对象。  
  
 `Tr`  
 字符特征。  
  
### <a name="return-value"></a>返回值  
 一个 `basic_ostream` 类型的对象。  
  
### <a name="remarks"></a>备注  
 该操控器调用 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Elem`( **'\0'**))。 返回 `Ostr.`  
  
### <a name="example"></a>示例  
  
```cpp  
// ostream_ends.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "a";  
   cout << "b" << ends;  
   cout << "c" << endl;  
}  
```  
  
```Output  
ab c  
```  
  
##  <a name="flush"></a>flush  
 刷新缓冲区。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& flush(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>参数  
 `Elem`  
 元素类型。  
  
 `Ostr`  
 一个 `basic_ostream` 类型的对象。  
  
 `Tr`  
 字符特征。  
  
### <a name="return-value"></a>返回值  
 一个 `basic_ostream` 类型的对象。  
  
### <a name="remarks"></a>备注  
 该操控器调用 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush)。 它将返回 `Ostr`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << flush;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="swap"></a>swap  
 交换两个 `basic_ostream` 对象的值。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 对 `basic_ostream` 对象的左值引用。  
  
 `right`  
 对 `basic_ostream` 对象的左值引用。  
  
### <a name="remarks"></a>备注  
 模板函数 `swap` 执行 `left.swap(right)`。  
  
## <a name="see-also"></a>另请参阅  
 [\<ostream>](../standard-library/ostream.md)


