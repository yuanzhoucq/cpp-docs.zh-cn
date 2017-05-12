---
title: "Platform::String 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String"
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::String 类
用于表示文本的 Unicode 字符的有序集合。 有关更多信息和示例，请参见[字符串](../cppcx/strings-c-cx.md)。  
  
## 语法  
  
```cpp  
  
public ref class String sealed : Object,  
    IDisposable,  
    IEquatable,  
    IPrintable  
```  
  
## 迭代器  
 两个迭代器函数（不是字符串类的成员）可以和 `std::for_each` 模板函数合用来枚举字符串对象中的字符。  
  
|成员|描述|  
|--------|--------|  
|`const char16* begin(String^ s)`|返回指向指定字符串对象开头的指针。|  
|`const char16* end(String^ s)`|返回通过指定字符串对象末尾的指针。|  
  
## 成员  
 此字符串类从对象、IDisposable、IEquatable 和 IPrintable 接口继承。  
  
 此字符串类还具有以下类型的成员。  
  
 **构造函数**  
  
|成员|描述|  
|--------|--------|  
|[String::String 构造函数](../cppcx/string-string-constructor.md)|初始化字符串类的新实例。|  
  
 **方法**  
  
 此字符串类从 [Platform::Object 类](../cppcx/platform-object-class.md) 继承 Equals\(\)、Finalize\(\), GetHashCode\(\)、GetType\(\)、MemberwiseClose\(\) 和 ToString\(\) 方法。 字符串还具有以下方法。  
  
|方法|说明|  
|--------|--------|  
|[String::Begin 方法](../cppcx/string-begin-method.md)|返回指向当前字符串开头的指针。|  
|[String::CompareOrdinal 方法](../cppcx/string-compareordinal-method.md)|通过估计对象所表示的两个字符值中相应字符的数字值来比较两个 `String` 对象。|  
|[String::Concat 方法](../cppcx/string-concat-method.md)|连接两个字符串对象的值。|  
|[String::Data 方法](../cppcx/string-data-method.md)|返回指向当前字符串开头的指针。|  
|[String::Dispose 方法](../cppcx/string-dispose-method.md)|释放资源。|  
|[String::End 方法](../cppcx/string-end-method.md)|返回通过当前字符串末尾的指针。|  
|[String::Equals 方法](../cppcx/string-equals-method.md)|指示指定对象是否等于当前对象。|  
|[String::GetHashCode 方法](../cppcx/string-gethashcode-method.md)|返回此实例的哈希代码。|  
|[String::IsEmpty 方法](../cppcx/string-isempty-method.md)|指示当前字符串对象是否为空。|  
|[String::IsFastPass 方法](../cppcx/string-isfastpass-method.md)|指示当前 String 对象是否参与*快速传递* 操作。 在快速传递操作中，将挂起引用计数。|  
|[String::Length 方法](../cppcx/string-length-method.md)|检索当前字符串对象的长度。|  
|[String::ToString 方法](../cppcx/string-tostring-method-c-cx.md)|返回一个字符串对象，其值与当前字符串相同。|  
  
 **属性**  
  
 此字符串类具有以下属性。  
  
|成员|描述|  
|--------|--------|  
|[String::operator\=\= 运算符](../cppcx/string-operator-equality-operator-c-cx.md)|指示指定的字符串对象是否具有相同的值。|  
|[operator\+ 运算符](../cppcx/string-operator-decrementoperator.md)|将两个字符串对象串联成一个新的字符串对象。|  
|[String::operator\> 运算符](../cppcx/string-operator-greater-than-operator-c-cx.md)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|  
|[String::operator\>\= 运算符](../cppcx/string-operator-greater-than-or-equals-c-cx.md)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|  
|[String::operator\!\= 运算符](../cppcx/string-operator-inequality-operator-c-cx.md)|指示两个指定字符串对象是否具有不同的值。|  
|[String::operator\< 运算符](../cppcx/string-operator-less-than-operator-c-cx.md)|指示一个字符串对象的值是否小于第二个字符串对象的值。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **头文件** vccorlib.h（默认包含在内）  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)