---
title: "wbuffer_convert 类 | Microsoft Docs"
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
  - "stdext::cvt::wbuffer_convert"
  - "wbuffer_convert"
  - "stdext.cvt.wbuffer_convert"
  - "cvt.wbuffer_convert"
  - "cvt::wbuffer_convert"
  - "wbuffer/stdext::cvt::wbuffer_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wbuffer_convert 类"
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wbuffer_convert 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述对元素与字节流缓冲区之间的来回传输进行控制的流缓冲区。  
  
## 语法  
  
```  
template<class Codecvt,  
    class Elem = wchar_t,  
    class Traits = std::char_traits<Elem>  
>  
    class wbuffer_convert  
        : public std::basic_streambuf<Elem, Traits>  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Codecvt`|表示转换对象的[区域设置](../standard-library/locale-class.md)方面。|  
|`Elem`|宽字符元素类型。|  
|`Traits`|与 *Elem* 关联的特征。|  
  
## 备注  
 此模板类描述对 `_Elem` 类型的元素（其字符特征由类 `Traits` 描述）与 `std::streambuf` 类型的字节流缓冲区之间的来回传输进行控制的流缓冲区。  
  
 一系列 `Elem` 值与多字节序列之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。  
  
 此模板类的对象存储：  
  
-   指向其基础字节流缓冲区的指针  
  
-   指向分配的转换对象（在 [wbuffer\_convert](../standard-library/wbuffer-convert-class.md) 对象销毁时释放）的指针  
  
-   [state\_type](../Topic/wbuffer_convert::state_type.md) 类型的转换状态对象。  
  
### 构造函数  
  
|||  
|-|-|  
|[wbuffer\_convert](../Topic/wbuffer_convert::wbuffer_convert.md)|构造 `wbuffer_convert` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[state\_type](../Topic/wbuffer_convert::state_type.md)|表示转换状态的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[rdbuf](../Topic/wbuffer_convert::rdbuf.md)|返回字节流缓冲区。|  
|[状态](../Topic/wbuffer_convert::state.md)|返回表示转换状态的对象。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:** std