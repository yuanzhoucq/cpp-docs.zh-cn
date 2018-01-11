---
title: "编译器错误 C3114 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3114
dev_langs: C++
helpviewer_keywords: C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 509c0dd1d85187871e78cfa93a66bc4ef385bbb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3114"></a>编译器错误 C3114
自变量： 不是有效的命名特性自变量  
  
 为了使属性类数据成员都是有效的命名自变量，它不能标记`static`， `const`，或`literal`。 如果某个属性，该属性不能`static`并且必须具有 get 和 set 访问器。  
  
 有关详细信息，请参阅[属性](../../windows/property-cpp-component-extensions.md)和[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3114。  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```