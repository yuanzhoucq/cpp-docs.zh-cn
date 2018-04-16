---
title: "Platform:: string 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c665b6767ea7a7a7d97d232f5253f8e182e6b0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="platformstring-class"></a>Platform::String 类
用于表示文本的 Unicode 字符的有序集合。 有关详细信息和示例，请参阅[字符串](../cppcx/strings-c-cx.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## <a name="iterators"></a>Iterators  
 两个迭代器函数（不是字符串类的成员）可以和 `std::for_each` 模板函数合用来枚举字符串对象中的字符。  
  
|成员|描述|  
|------------|-----------------|  
|`const char16* begin(String^ s)`|返回指向指定字符串对象开头的指针。|  
|`const char16* end(String^ s)`|返回通过指定字符串对象末尾的指针。|  
  
### <a name="members"></a>成员  
 此字符串类从对象、IDisposable、IEquatable 和 IPrintable 接口继承。  
  
 此字符串类还具有以下类型的成员。  
  
 **构造函数**  
  
|成员|描述|  
|------------|-----------------|  
|[String::String](#ctor)|初始化字符串类的新实例。|  
  
 **方法**  
  
 此字符串类从 [Platform::Object Class](../cppcx/platform-object-class.md)继承 Equals()、Finalize(), GetHashCode()、GetType()、MemberwiseClose() 和 ToString() 方法。 字符串还具有以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[String::Begin](#begin)|返回指向当前字符串开头的指针。|  
|[String::CompareOrdinal](#compareordinal)|通过估计对象所表示的两个字符值中相应字符的数字值来比较两个 `String` 对象。|  
|[String::Concat](#concat)|连接两个字符串对象的值。|  
|[String::Data](#data)|返回指向当前字符串开头的指针。|  
|[String::Dispose](#dispose)|释放资源。|  
|[String::End](#end)|返回通过当前字符串末尾的指针。|  
|[String::Equals](#equals)|指示指定对象是否等于当前对象。|  
|[String::GetHashCode](#gethashcode)|返回此实例的哈希代码。|  
|[String::IsEmpty](#isempty)|指示当前字符串对象是否为空。|  
|[String::IsFastPass](#isfastpass)|指示当前 String 对象是否参与 *快速传递* 操作。 在快速传递操作中，将挂起引用计数。|  
|[String::Length](#length)|检索当前字符串对象的长度。|  
|[String::ToString](#tostring)|返回一个字符串对象，其值与当前字符串相同。|  
  
 **运算符**  
  
 此字符串类具有以下运算符。  
  
|成员|描述|  
|------------|-----------------|  
|[String:: operator = = 运算符](#operator-equality)|指示指定的字符串对象是否具有相同的值。|  
|[operator+ 运算符](#operator-plus)|将两个字符串对象串联成一个新的字符串对象。|  
|[String:: operator > 运算符](#operator-greater-than)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|  
|[String:: operator > = 运算符](#operator-greater-than-or-equals)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|  
|[String:: operator ！ = 运算符](#operator-inequality)|指示两个指定字符串对象是否具有不同的值。|  
|[String:: operator < 运算符](#operator-less-than)|指示一个字符串对象的值是否小于第二个字符串对象的值。|  
  
### <a name="requirements"></a>惠?  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **头文件** vccorlib.h（默认包含在内）  

 
## <a name="begin"></a>  String:: begin 方法
返回指向当前字符串开头的指针。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
char16* Begin()  
```  
  
### <a name="return-value"></a>返回值  
 指向当前字符串开头的指针。  
  
## <a name="compareordinal"></a>  String:: compareordinal 方法
通过估计对象所表示的两个字符值中相应字符的数字值来比较两个 `String` 对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 一个整数，指示两个比较字之间的词法关系。 下表列出可能的返回值。  
  
|“值”|条件|  
|-----------|---------------|  
|-1|`str1` 小于 `str2`。|  
|0|`str1` 等于 `str2`。|  
|1|`str1` 大于 `str2`。|  
  


## <a name="concat"></a>  String:: concat 方法
连接两个字符串对象的值。  
  
### <a name="syntax"></a>语法  
  
```cpp    
String^ Concat( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串对象或 `null`。  
  
 `str2`  
 第二个字符串对象或 `null`。  
  
### <a name="return-value"></a>返回值  
 其值为 `str1` 与 `str2` 的值相连的新 String^ 对象。  
  
 如果`str1`是`null`和`str2`不是，`str1`返回。 如果`str2`是`null`和`str1`不是，`str2`返回。 如果 `str1` 和 `str2` 都是 `null`，则返回空字符串 (L "")。  
  


## <a name="data"></a>  String:: data 方法
以 C 样式 `char16` (`wchar_t`) 元素数组的形式返回指向对象的数据缓冲区开头的指针。  
  
### <a name="syntax"></a>语法  
  
```  
const char16* Data()  
```  
  
### <a name="return-value"></a>返回值  
 开头的指针`const char16`的 Unicode 字符数组 (`char16`是的 typedef `wchar_t`)。  
  
### <a name="remarks"></a>备注  
 使用此方法可从 `Platform::String^` 转换为 `wchar_t*`。 当 `String` 对象超出范围时，数据指针不再保证有效。 用于存储数据的原始生存期以外`String`对象，请使用[wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)数组复制到您为自己分配的内存。  
  


## <a name="dispose"></a>  String:: dispose 方法
释放资源。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
virtual override void Dispose()  
```  

## <a name="end"></a>  String:: end 方法
返回通过当前字符串末尾的指针。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
char16* End()  
```  
  
### <a name="return-value"></a>返回值  
 指向超出当前字符串末尾的指针。  
  
### <a name="remarks"></a>备注  
 End （） 返回 begin （） + 长度。  
  


## <a name="equals"></a>  String:: equals 方法
指示指定的字符串是否具有和当前对象相同的值。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
### <a name="parameters"></a>参数  
 `str`  
 要比较的对象。  
  
### <a name="return-value"></a>返回值  
 如果 `true` 等于当前对象，则为 `str`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法相当于[string:: compareordinal](#compareordinal)。 在第一个重载中，`str` 参数应能够转换为 String^ 对象。  
  


## <a name="gethashcode"></a>  String::GetHashCode Method
返回此实例的哈希代码。  
  
### <a name="syntax"></a>语法  
  
```cpp  
  
virtual override int GetHashCode()  
```  
  
### <a name="return-value"></a>返回值  
 此实例的哈希代码。  
  


## <a name="isempty"></a>  String:: isempty 方法
指示当前字符串对象是否为空。  
  
### <a name="syntax"></a>语法  
  
```cpp    
bool IsEmpty()  
```  
  
### <a name="return-value"></a>返回值  
 如果当前字符串对象是 `true` 或为空字符串 (L "")，则为 `null`；否则，为 `false`。  
  


## <a name="isfastpass"></a>  String:: isfastpass 方法
指示当前 String 对象是否参与 *快速传递* 操作。 在快速传递操作中，将挂起引用计数。  
  
### <a name="syntax"></a>语法  
  
```cpp    
bool IsFastPass();  
```  
  
### <a name="return-value"></a>返回值  
 如果当前 String 对象已快速传递，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 在引用计数对象作为参数并且被调用的函数只读取该对象的函数调用中，编译器可以安全地挂起引用计数并改进调用性能。 没有可供您的代码对此属性执行的任何操作。 系统处理所有详细信息。  
  


## <a name="length"></a>  String:: length 方法
检索当前字符串对象中的字符数。  
  
### <a name="syntax"></a>语法  
  
```cpp    
unsigned int Length()  
```  
  
### <a name="return-value"></a>返回值  
 当前字符串对象中的字符数。  
  
### <a name="remarks"></a>备注  
 一个没有字符的字符串的长度为零。 以下字符串的长度为 5：  
  
```    
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 返回的字符数组[string:: data](#data)具有一个附加字符，是终止 NULL 或 \0'。 该字符也是两个字节长。  
  


## <a name="operator-plus"></a>  String::operator+ Operator
串联两个[字符串](../cppcx/platform-string-class.md)到新的对象[字符串](../cppcx/platform-string-class.md)对象。
  
### <a name="syntax"></a>语法  
  
```cpp  
  
bool String::operator+( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个 `String` 对象。  
  
 `str2`  
 第二个 `String` 对象，其内容将追加到 `str1`。  
  
### <a name="return-value"></a>返回值  
 如果 `true` 等于 `str1`，则为 `str2`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此运算符创建一个 `String^` 对象，用以包含两个操作数中的数据。 在极端性能并不重要时，使用它只是为了方便。 函数中有些对“`+`”的调用可能不明显，但如果在紧凑循环中操作大对象或文本数据，则使用标准 C++ 机制和类型。  
  
##  <a name="operator-equality"></a> String::operator== Operator
指示指定的字符串对象是否具有相同的文本值。  
  
### <a name="syntax"></a>语法  
  
```cpp    
bool String::operator==( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 要比较的第一个字符串对象。  
  
 `str2`  
 要比较的第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 如果 `true` 的内容等于 `str1`，则为 `str2`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此运算符相当于[string:: compareordinal](#compareordinal)。  
  


##  <a name="operator-greater-than"></a>  String::operator&gt; 
指示一个字符串对象的值是否大于或等于第二个字符串对象的值。  
  
### <a name="syntax"></a>语法  
  
```cpp    
bool String::operator>( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 如果 `str1` 的值大于 `str2` 的值，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此运算符与显式调用相当[string:: compareordinal](#compareordinal)并得到大于零的结果。  
  


## <a name="operator-greater-than-or-equals"></a> String::operator&gt;= 
指示一个字符串对象的值是否大于或等于第二个字符串对象的值。  
  
### <a name="syntax"></a>语法  
  
```cpp    
bool String::operator>=( String^ str1, String^ str2) 
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 如果 `str1` 的值大于或等于 `str2` 的值，则为 `true`；否则为 `false`。  
  


## <a name="operator-inequality"></a> String::operator!= 
指示两个指定字符串对象是否具有不同的值。  
  
### <a name="syntax"></a>语法  
  
```cpp  
bool String::operator!=( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 要比较的第一个字符串对象。  
  
 `str2`  
 要比较的第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 如果 `true` 不等于 `str1`，则为 `str2`；否则为 `false`。   


## <a name="operator-less-than"></a> String::operator&lt; 
指示一个字符串对象的值是否小于第二个字符串对象的值。  
  
### <a name="syntax"></a>语法  
  
```cpp  
bool String::operator<( String^ str1, String^ str2)  
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
### <a name="return-value"></a>返回值  
 如果 `str1` 的值小于 `str2` 的值，则为 `true`；否则为 `false`。  
  
## <a name="ctor"></a> String:: string 构造函数
使用输入字符串数据初始化字符串类的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp    
String();    
String(char16* s)  
String(char16* s, unsigned int n)  
```  
  
### <a name="parameters"></a>参数  
 `s`  
 初始化字符串的一系列宽字符。 char16  
  
 `n`  
 指定字符串长度的一个数字。  
  
### <a name="remarks"></a>备注  
 如果性能非常重要而且你控制源字符串的生存期，则可以使用[platform:: stringreference](../cppcx/platform-stringreference-class.md)代替 String。  
### <a name="example"></a>示例  
  
```cpp  
String^ s = L"Hello!";  
```  
  
## <a name="tostring"></a> String::ToString
返回一个字符串对象，其值与当前字符串相同。  
  
### <a name="syntax"></a>语法  
  
```cpp  
String^ String::ToString()  
```  
  
### <a name="return-value"></a>返回值  
 其值与当前字符串相同的字符串对象。  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)