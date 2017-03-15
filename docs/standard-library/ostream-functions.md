---
title: "&lt;ostream&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 15
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 44708461657101b1ddad7db76f1c3c8d4df07f3a
ms.lasthandoff: 02/24/2017

---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函数
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ends](#ends)|  
|[flush](#flush)|  
  
##  <a name="a-nameendla--endl"></a><a name="endl"></a>endl  
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
 该操控器调用 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#basic_ostream__put)( `Ostr`**.** [widen](../standard-library/basic-ios-class.md#basic_ios__widen)( **'\n'**))，然后调用 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#basic_ostream__flush)。 它将返回 `Ostr`。  
  
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
  
##  <a name="a-nameendsa--ends"></a><a name="ends"></a>  ends  
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
 该操控器调用 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#basic_ostream__put)( `Elem`( **'\0'**))。 返回 `Ostr.`  
  
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
  
##  <a name="a-nameflusha--flush"></a><a name="flush"></a>flush  
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
 该操控器调用 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#basic_ostream__flush)。 它将返回 `Ostr`。  
  
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
  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>swap  
 交换两个 `basic_ostream` 对象的值。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 对 `basic_ostream` 对象的左值引用。  
  
 ` right`  
 对 `basic_ostream` 对象的左值引用。  
  
### <a name="remarks"></a>备注  
 模板函数 `swap` 执行 ` left.swap(`` right``)`。  
  
## <a name="see-also"></a>另请参阅  
 [\<ostream>](../standard-library/ostream.md)


