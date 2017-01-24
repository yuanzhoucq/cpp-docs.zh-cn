---
title: "codecvt_base 类 | Microsoft Docs"
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
  - "codecvt_base"
  - "xlocale/std::codecvt_base"
  - "std.codecvt_base"
  - "std::codecvt_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_base 类"
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于定义称为的枚举类型 **result**的 codecvt 类的基类，它使用，个成员的返回类型指示函数转换的结果。  
  
## 语法  
  
```  
class codecvt_base : public locale::facet {  
public:  
    enum result {ok, partial, error, noconv};  
    codecvt_base(  
        size_t _Refs = 0  
);  
    bool always_noconv() const;  
    int max_length() const;  
    int encoding() const;  
    ~codecvt_base()  
protected:  
    virtual bool do_always_noconv() const;  
    virtual int do_max_length() const;  
    virtual int do_encoding() const;  
};  
```  
  
## 备注  
 类描述了枚举共有类模板所有专用化的 [codecvt](../standard-library/codecvt-class.md)。  描述枚举结果或从 [do\_in](../Topic/codecvt::do_in.md)[do\_out](../Topic/codecvt::do_out.md)的返回值：  
  
-   **确定**，则在内部和外部字符编码之间的强制转换成功。  
  
-   **部分**，则目标不足以用于转换成功。  
  
-   **错误**，如果源序列的格式错误。  
  
-   **noconv**，如果函数不执行转换。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)