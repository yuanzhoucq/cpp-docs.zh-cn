---
title: "可变数据成员 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b51f53444b7482575398b68c3a2bf52b3de96e55
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="mutable-data-members-c"></a>可变数据成员 (C++)
此关键字只能应用于类的非静态和非常量数据成员。 如果声明数据成员`mutable`，则它是合法将值分配给从该数据成员**const**成员函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>备注  
 例如，以下代码在编译时不会出错，因为 `m_accessCount` 已声明为 `mutable`，因此可以由 `GetFlag` 修改，即使 `GetFlag` 是常量成员函数。  
  
```  
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
