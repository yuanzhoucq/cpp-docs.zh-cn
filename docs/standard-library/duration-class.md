---
title: "duration 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::duration"
dev_langs: 
  - "C++"
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# duration 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述存放一个 *时间间隔*，在两个时间点之间的一个过去时间点类型.  
  
## 语法  
  
```  
template<  
   class Rep,  
   class Period = ratio<1>  
>  
class duration;  
template<  
   class Rep,  
   class Period  
>  
class duration;  
template<  
   class Rep,  
   class Period1,  
   class Period2  
>  
class duration  
   <duration<Rep, Period1>, Period2>;  
```  
  
## 备注  
 模板参数 `Rep` 描述用于保存时钟滴答周期数在间隔的类型。  模板参数 `Period` 是描述间隔大小的刻度表示 [比例](../standard-library/ratio.md) 的实例化。  
  
## 成员  
  
### 公共 Typedef  
  
|Name|说明|  
|----------|--------|  
|[duration::period Typedef](http://msdn.microsoft.com/zh-cn/ebf2a1b9-769f-475f-8c66-cf9ed12015f2)|表示模板参数的 `Period`同义词。|  
|[duration::rep Typedef](http://msdn.microsoft.com/zh-cn/f47b8abb-ae2c-4dc8-858a-f44695156950)|表示模板参数的 `Rep`同义词。|  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[duration::duration 构造函数](../Topic/duration::duration%20Constructor.md)|构造 `duration` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[duration::count 方法](../Topic/duration::count%20Method.md)|返回在时间间隔中时钟计时周期的次数.|  
|[duration::max 方法](../Topic/duration::max%20Method.md)|静态的。  返回模板参数 `Ref`的最大允许的值。|  
|[duration::min 方法](../Topic/duration::min%20Method.md)|静态的。  返回模板参数 `Ref`的最小允许的值。|  
|[duration::zero 方法](../Topic/duration::zero%20Method.md)|静态的。  实际上，返回 `Rep`\(0\)。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[duration::operator\- 运算符](../Topic/duration::operator-%20Operator.md)|返回连同否定滴答计数 `duration` 对象的副本。|  
|[duration::operator\-\- 运算符](../Topic/duration::operator--%20Operator.md)|递减存储的滴答计数。|  
|[duration::operator\= Operator](../Topic/duration::operator=%20Operator.md)|减少存储的滴答计数的模数指定值。|  
|[duration::operator\*\= Operator](../Topic/duration::operator*=%20Operator.md)|通过指定的值乘上存储的滴答计数值。|  
|[duration::operator\/\= 运算符](../Topic/duration::operator-=%20Operator1.md)|由指定的 `duration` 对象的滴答计数部件存储的滴答计数。|  
|[duration::operator\+ 运算符](../Topic/duration::operator+%20Operator.md)|返回 `*this`。|  
|[duration::operator\+\+ 运算符](../Topic/duration::operator++%20Operator.md)|存储的滴答计数的增量。|  
|[duration::operator\+\= Operator](../Topic/duration::operator+=%20Operator.md)|把指定的 `duration` 对象的滴答计数添加到存储的滴答计数。|  
|[duration::operator\-\= Operator](../Topic/duration::operator-=%20Operator2.md)|从存储的滴答计数值中减去指定的 `duration` 对象的滴答计数。|  
  
## 要求  
 **Header:** chrono  
  
 **Namespace:** std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [duration\_values 结构](../standard-library/duration-values-structure.md)