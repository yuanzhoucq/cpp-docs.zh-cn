---
title: "ctype &lt; char &gt; 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ctype<char>"
  - "locale/std::ctype<char>"
  - "std::ctype<char>"
  - "std.ctype<char>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype < char > 类"
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype &lt; char &gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类是模板类的显式专用化 **ctype \< CharType**> 键入 `char`, ，描述一个对象来充当区域设置 facet，以鉴定的类型的字符的各种属性 `char`。  
  
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
 以下几种方式与模板类显式专用化不同︰  
  
-   Ctype 类的对象 < `char`> 存储 ctype 掩码表的第一个元素，数组 UCHAR_MAX + 1 个元素的类型指针 **ctype_base::mask**。 它还存储布尔对象，该值指示是否应删除数组 (使用 `operator delete[]`) 时 ctype \< **Elem**> 对象被销毁。  
  
-   其唯一的公共构造函数允许你指定 **选项卡**, ，ctype 掩码表格和 **del**, ，如果数组应为 true 的 Boolean 对象时删除 ctype < `char`> 对象被销毁，以及引用计数参数 refs。  
  
-   受保护的成员函数 **表** 返回存储的 ctype 掩码表。  
  
-   静态成员对象 **table_size** ctype 掩码表中指定的最小元素数。  
  
-   受保护的静态成员函数 **classic_table**（返回 ctype 掩码表适合于"C"区域设置。  
  
-   没有受保护虚拟成员函数 [do_is](../standard-library/ctype-class.md#ctype__do_is), ，[do_scan_is](../standard-library/ctype-class.md#ctype__do_scan_is), ，或 [do_scan_not](../standard-library/ctype-class.md#ctype__do_scan_not)。 对应的公共成员函数执行等效操作本身。  
  
 成员函数 [do_narrow](../standard-library/ctype-class.md#ctype__do_narrow) 和 [do_widen](../standard-library/ctype-class.md#ctype__do_widen) 复制不变的元素。  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [facet 类](../Topic/facet%20Class.md)   
 [ctype_base 类](../standard-library/ctype-base-class.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

