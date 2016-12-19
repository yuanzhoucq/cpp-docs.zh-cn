---
title: "CA2AEX 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CA2AEX<t_nBufferLength>"
  - "CA2AEX"
  - "ATL.CA2AEX<t_nBufferLength>"
  - "ATLCONV/CA2AEX"
  - "ATL.CA2AEX"
  - "ATL::CA2AEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2AEX 类"
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CA2AEX 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字符串翻译宏 `CA2TEX` 和 `CT2AEX`和typedef使用此选件类 **CA2A**。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2AEX  
```  
  
#### 参数  
 `t_nBufferLength`  
 用于的缓冲区的大小将过程。  默认长度为128个字节。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CA2AEX::CA2AEX](../Topic/CA2AEX::CA2AEX.md)|构造函数。|  
|[CA2AEX::~CA2AEX](../Topic/CA2AEX::~CA2AEX.md)|该析构函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CA2AEX::operator LPSTR](../Topic/CA2AEX::operator%20LPSTR.md)|转换运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CA2AEX::m\_psz](../Topic/CA2AEX::m_psz.md)|存储源字符串的数据成员。|  
|[CA2AEX::m\_szBuffer](../Topic/CA2AEX::m_szBuffer.md)|静态缓冲区，用于存储已转换的字符串。|  
  
## 备注  
 除非需要额外功能，使用 `CA2TEX`，`CT2AEX`或 **CA2A** 在代码。  
  
 此选件类包含用于存储转换的结果的固定大小的静态缓冲区。  如果结果太大而无法放入该静态缓冲区，使用 `malloc`，选件类分配内存，释放内存，当对象超出范围。  这样可确保不同，文本转换宏有ATL的早期版本中，此选件类是安全使用在循环中，它不会溢出堆栈。  
  
 如果选件类尝试分配堆上分配内存失败，它将调用与 **E\_OUTOFMEMORY**参数的 `AtlThrow`。  
  
 默认情况下，ATL转换选件类和宏来转换使用当前线程的ANSI代码页。  
  
 下面的宏基于此选件类:  
  
-   `CA2TEX`  
  
-   `CT2AEX`  
  
 下面的typedef基于此选件类:  
  
-   **CA2A**  
  
 有关这些讨论的文本翻译宏，请参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 示例  
 为使用基于这些字符串翻译宏参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 要求  
 **Header:** atlconv.h  
  
## 请参阅  
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)