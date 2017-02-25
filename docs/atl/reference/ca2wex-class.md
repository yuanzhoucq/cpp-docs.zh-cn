---
title: "CA2WEX 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLCONV/CA2WEX"
  - "ATL.CA2WEX"
  - "ATL.CA2WEX<t_nBufferLength>"
  - "ATL::CA2WEX"
  - "ATL::CA2WEX<t_nBufferLength>"
  - "CA2WEX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CA2WEX 类"
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CA2WEX 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字符串翻译宏使用此选件类 `CA2TEX`、 `CA2CTEX`、 `CT2WEX`和 `CT2CWEX`和typedef **CA2W**。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
int t_nBufferLength= 128  
>  
class CA2WEX  
```  
  
#### 参数  
 `t_nBufferLength`  
 用于的缓冲区的大小将过程。  默认长度为128个字节。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CA2WEX::CA2WEX](../Topic/CA2WEX::CA2WEX.md)|构造函数。|  
|[CA2WEX::~CA2WEX](../Topic/CA2WEX::~CA2WEX.md)|该析构函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CA2WEX::operator LPWSTR](../Topic/CA2WEX::operator%20LPWSTR.md)|转换运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CA2WEX::m\_psz](../Topic/CA2WEX::m_psz.md)|存储源字符串的数据成员。|  
|[CA2WEX::m\_szBuffer](../Topic/CA2WEX::m_szBuffer.md)|静态缓冲区，用于存储已转换的字符串。|  
  
## 备注  
 除非需要额外功能，使用 `CA2TEX`，`CA2CTEX`、 `CT2WEX`、 `CT2CWEX`或 **CA2W** 在您的代码。  
  
 此选件类包含用于存储转换的结果的固定大小的静态缓冲区。  如果结果太大而无法放入该静态缓冲区，使用 `malloc`，选件类分配内存，释放内存，当对象超出范围。  这样可确保不同，文本转换宏有ATL的早期版本中，此选件类是安全使用在循环中，它不会溢出堆栈。  
  
 如果选件类尝试分配堆上分配内存失败，它将调用与 **E\_OUTOFMEMORY**参数的 `AtlThrow`。  
  
 默认情况下，ATL转换选件类和宏来转换使用当前线程的ANSI代码页。  如果要重写特定将此行为，请指定代码页作为第二个参数传递给构造函数。选件类。  
  
 下面的宏基于此选件类:  
  
-   `CA2TEX`  
  
-   `CA2CTEX`  
  
-   `CT2WEX`  
  
-   `CT2CWEX`  
  
 下面的typedef基于此选件类:  
  
-   **CA2W**  
  
 有关这些讨论的文本翻译宏，请参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 示例  
 为使用基于这些字符串翻译宏参见 [ATL和MFC字符串翻译宏](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)。  
  
## 要求  
 **Header:** atlconv.h  
  
## 请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)