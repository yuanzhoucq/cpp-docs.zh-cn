---
title: _com_ptr_t 提取器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8414fb0e3478b5aae906db3e511757d5d7df71d3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404091"
---
# <a name="comptrt-extractors"></a>_com_ptr_t 提取器
**Microsoft 专用**  
  
 提取封装的 COM 接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## <a name="remarks"></a>备注  
  
-   **运算符接口\*** 返回封装的接口指针，这可能为 NULL。  
  
-   **运算符接口 &** 返回对封装的接口指针的引用，并发出错误，如果指针为 NULL。  
  
-   **运算符\*** 允许智能指针对象在执行操作，就好像它是实际封装的接口取消引用时。  
  
-   **运算符->** 允许智能指针对象在执行操作，就好像它是实际封装的接口取消引用时。  
  
-   **运算符 &** 释放所有封装的接口指针，将它替换为 NULL，并返回封装的指针的地址。 这允许智能指针通过寻址传递到具有的函数*出*参数通过它会返回一个接口指针。  
  
-   **运算符 bool**允许智能指针对象在条件表达式中使用。 如果指针不为 NULL，则此运算符返回 TRUE。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)