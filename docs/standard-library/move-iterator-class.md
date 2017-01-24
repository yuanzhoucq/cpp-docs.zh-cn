---
title: "move_iterator 类 | Microsoft Docs"
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
  - "std.move_iterator"
  - "move_iterator"
  - "iterator/std::move_iterator"
  - "std::move_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "move_iterator 类"
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: 20
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# move_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类模板 `move_iterator` 是迭代器的包装器。  move\_iterator 的行为与其包装（存储）的迭代器相同，但它将存储的迭代器的取消引用运算符转换为右值引用，将副本转换为移动。  有关右值的详细信息，请参阅[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 语法  
  
```  
template<class Iterator>  
    class move_iterator {  
public:  
    typedef Iterator iterator_type;  
    typedef typename      
        iterator_traits<Iterator>::iterator_category  
            iterator_category;  
    typedef typename iterator_traits<Iterator>::value_type  
        value_type;  
    typedef typename iterator_traits<Iterator>::difference_type  
        difference_type;  
    typedef Iterator  
        pointer;  
    typedef value_type&&  
        reference;  
  
    move_iterator();  
    explicit move_iterator (Iterator right);  
    template<class Type>  
        move_iterator (const move_iterator<Type>& right);  
    template <class Type>   
        move_iterator& operator=(const move_iterator<Type>& right);  
  
    iterator_type base () const;  
    reference operator* () const;  
    pointer operator-> () const;  
  
    move_iterator& operator++ ();  
    move_iterator operator++ (int);  
    move_iterator& operator-- ();  
    move_iterator operator-- (int);  
  
    move_iterator& operator+= (difference_type off);  
    move_iterator operator+ (difference_type off) const;  
    move_iterator& operator-= (difference_type off);  
    move_iterator operator- (difference_type off) const;  
    reference operator[] (difference_type off) const;  
    };  
```  
  
## 备注  
 模板类描述在行为上与迭代器类似（取消引用时除外）的对象。  它存储 `Iterator` 类型的随机访问迭代器，可通过成员函数 `base``()` 访问此迭代器。  对于 `move_iterator` 的所有操作将直接对存储的迭代器执行，但 `operator*` 的结果将隐式强制转换为 `value_type&&` 以进行右值引用。  
  
 `move_iterator` 可以进行包装的迭代器未定义的操作。  不应使用这些操作。  
  
### 构造函数  
  
|||  
|-|-|  
|[move\_iterator](../Topic/move_iterator::move_iterator.md)|`move_iterator` 类型的对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[move\_iterator::iterator\_type](../Topic/move_iterator::iterator_type.md)|模板参数 `RandomIterator` 的同义词。|  
|[move\_iterator::iterator\_category](../Topic/move_iterator::iterator_category.md)|同一名称的较长 `typename` 表达式的同义词，`iterator_category` 用于标识迭代器的常规功能。|  
|[move\_iterator::value\_type](../Topic/move_iterator::value_type.md)|同一名称的较长 `typename` 表达式的同义词，`value_type` 用于描述迭代器元素的类型。|  
|[move\_iterator::difference\_type](../Topic/move_iterator::difference_type.md)|同一名称的较长 `typename` 表达式的同义词，`difference_type` 用于描述表示元素间的差值所需的整型。|  
|[move\_iterator::pointer](../Topic/move_iterator::pointer.md)|模板参数 `RandomIterator` 的同义词。|  
|[move\_iterator::reference](../Topic/move_iterator::reference.md)|`rvalue` 引用 `value_type&&` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[move\_iterator::base](../Topic/move_iterator::base.md)|此成员函数返回该 `move_iterator` 包装的存储迭代器。|  
  
### 运算符  
  
|||  
|-|-|  
|[move\_iterator::operator\*](../Topic/move_iterator::operator*.md)|返回 `(reference)*``base``()`。|  
|[move\_iterator::operator\+\+](../Topic/move_iterator::operator++.md)|递增存储的迭代器。  确切行为取决于它是前置递增操作还是后置递增操作。|  
|[move\_iterator::operator\-\-](../Topic/move_iterator::operator--.md)|递减存储的迭代器。  确切行为取决于它是前置递减操作还是后置递减操作。|  
|[move\_iterator::operator\-\>](../Topic/move_iterator::operator-%3E.md)|返回 `&**this`。|  
|[move\_iterator::operator\-](../Topic/move_iterator::operator-.md)|通过先从当前位置减去右值来返回 `move_iterator(*this) -=` 。|  
|[move\_iterator::operator](../Topic/move_iterator::operator.md)|返回 `(reference)*(*this + off)`。  允许你指定相对于当前基础位置的偏移量以获取位于偏移位置的值。|  
|[move\_iterator::operator\+](../Topic/move_iterator::operator+.md)|返回 `move_iterator(*this) +=` 值。  允许你向基础位置添加偏移量以获取位于偏移位置的值。|  
|[move\_iterator::operator\+\=](../Topic/move_iterator::operator+=.md)|将右值添加到存储的迭代器，并返回 `*this`。|  
|[move\_iterator::operator\-\=](../Topic/move_iterator::operator-=.md)|从存储的迭代器减去右值，并返回 `*this`。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [移动构造函数和移动赋值运算符 \(C\+\+\)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [标准模板库](../misc/standard-template-library.md)