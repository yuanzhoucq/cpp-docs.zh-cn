---
title: "ctype&lt;char&gt; 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
- std::ctype<char>
- std.ctype<char>
dev_langs:
- C++
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 0acae30ecbe670c87179f4cc2f5a2b8066ef3a4c
ms.lasthandoff: 02/24/2017

---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; 类
该类将 **ctype\<CharType**> 的模板类显式专用化为 `char` 类型，它描述一个对象来充当区域设置 facet，用来将 `char` 类字符的各种属性特征化。  
  
## <a name="syntax"></a>语法  
  
```  
template <>  
class ctype<char>  
: public ctype_base  
{  
public:  
    typedef char _Elem;  
    typedef _Elem char_type;  
    bool is(
    mask _Maskval,  
    _Elem _Ch) const;

 
    const _Elem* is(
    const _Elem* first,  
    const _Elem* last,  
    mask* dest) const;

 
    const _Elem* scan_is(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    const _Elem* scan_not(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    _Elem tolower(
    _Elem _Ch) const;

 
    const _Elem* tolower(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem toupper(
    _Elem _Ch) const;

 
    const _Elem* toupper(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem widen(
    char _Byte) const;

 
    const _Elem* widen(
    const char* first,  
    const char* last,  
    _Elem* dest) const;

 
    const _Elem* _Widen_s(
    const char* first,  
    const char* last,  
    _Elem* dest,  
    size_t dest_size) const;

 
    _Elem narrow(
    _Elem _Ch,  
    char _Dflt = '\0') const;

 
    const _Elem* narrow(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest) const;

 
    const _Elem* _Narrow_s(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest,  
    size_t dest_size) const;

 
    static locale::id& id;  
    explicit ctype(
    const mask* _Table = 0,  
    bool _Deletetable = false,  
    size_t _Refs = 0);

protected:  
    virtual ~ctype();
//other protected members  
};  
```  
  
## <a name="remarks"></a>备注  
 显式专用化与模板类存在以下几个方面的差异：  
  
-   ctype< `char`> 类对象将指针存储到 ctype 掩码表的第一个元素，该掩码表是 **ctype_base::mask** 类型的 UCHAR_MAX + 1 元素数组。 它还存储布尔对象，指明当 ctype\< **Elem**> 对象被销毁时是否应（使用 `operator delete[]`）删除数组。  
  
-   其唯一的公共构造函数允许指定 ctype 掩码表 **tab** 和布尔对象 **del**，如果在销毁 ctype< `char`> 对象时应删除该数组，则布尔对象为 true，还会指定 reference-count 参数引用。  
  
-   受保护的成员函数 **table** 返回存储的 ctype 掩码表。  
  
-   静态成员对象 **table_size** 在 ctype 掩码表中指定最小的元素数。  
  
-   受保护的静态成员函数 **classic_table** 返回适合于 “C” 区域设置的 ctype 掩码表。  
  
-   没有受保护的虚拟成员函数 [do_is](../standard-library/ctype-class.md#ctype__do_is)、[do_scan_is](../standard-library/ctype-class.md#ctype__do_scan_is)，或 [do_scan_not](../standard-library/ctype-class.md#ctype__do_scan_not)。 相应的公共成员函数自身执行等效操作。  
  
 成员函数 [do_narrow](../standard-library/ctype-class.md#ctype__do_narrow) 和 [do_widen](../standard-library/ctype-class.md#ctype__do_widen) 复制未改变的元素。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [facet 类](http://msdn.microsoft.com/Library/dd4f12f5-cb1b-457f-af56-2fb204216ec1)   
 [ctype_base 类](../standard-library/ctype-base-class.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


