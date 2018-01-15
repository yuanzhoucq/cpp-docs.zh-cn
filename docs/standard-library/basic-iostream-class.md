---
title: "basic_iostream 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs: C++
helpviewer_keywords: basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d415afefbde1f3903450a7c5e9f8f14e5cb78a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="basiciostream-class"></a>basic_iostream 类
可以完成输入和输出的流类。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>备注  
 此模板类描述一个对象，该对象通过其基类 [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> 控制插入并通过其基类 [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`> 控制提取。 两个对象共享一个公共的虚拟基类 [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>。 他们还管理通用流缓冲区与类型为 `Elem` 的元素，其字符特征由类 `Tr` 确定。 构造函数会通过 `basic_istream`( **strbuf**) 和 `basic_ostream`( **strbuf**) 初始化其基类。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream)|创建 `basic_iostream` 对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[swap](#swap)|将所提供 `basic_iostream` 对象的内容与此对象的内容交换。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#op_eq)|将指定的 `basic_iostream` 对象的值分配给此对象。 这是一种移动赋值，所涉及的 `rvalue` 不会留下副本。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<istream>  
  
 **命名空间：** std  
  
##  <a name="basic_iostream"></a>  basic_iostream::basic_iostream  
 创建 `basic_iostream` 对象。  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>参数  
 `strbuf`  
 一个现有的 `basic_streambuf` 对象。  
  
 `right`  
 用于构造新 `basic_iostream` 的现有 `basic_iostream` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过 `basic_istream(strbuf)` 和 `basic_ostream(strbuf)` 初始化基对象。  
  
 第二个构造函数初始化基对象通过调用`move(right)`。  
  
##  <a name="op_eq"></a>  basic_iostream::operator=  
 将指定的 `basic_iostream` 对象的值赋给此对象。 这是一种移动赋值，所涉右值不会留下副本。  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 对从其中进行赋值的 `basic_iostream` 对象的 `rvalue` 引用。  
  
### <a name="remarks"></a>备注  
 成员运算符调用`swap(right)`。  
  
##  <a name="swap"></a>  basic_iostream::swap  
 将所提供 `basic_iostream` 对象的内容与此对象的内容交换。  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要交换的 `basic_iostream` 对象。  
  
### <a name="remarks"></a>备注  
 此成员函数调用`swap(right)`。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)

