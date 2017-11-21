---
title: "_com_ptr_t 提取器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs: C++
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
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73e2dca693939765e700d51b6caab0815c6d5e7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
-   **运算符接口\***返回封装的接口指针，这可能是**NULL**。  
  
-   **运算符接口 （& a)**返回对封装的接口指针的引用，并发出错误，如果指针**NULL**。  
  
-   **运算符\***允许智能指针对象在充当实际封装的接口取消引用时。  
  
-   **operator->**允许智能指针对象在充当实际封装的接口取消引用时。  
  
-   **运算符 &**释放任何封装的接口指针，将其替换为**NULL**，并返回封装的指针的地址。 这允许智能指针通过寻址传递到具有的函数**出**参数通过其它将返回的接口指针。  
  
-   **运算符 bool**允许智能指针对象在条件表达式中使用。 此运算符返回**true**如果指针不**NULL**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)