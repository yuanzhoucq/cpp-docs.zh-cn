---
title: "is、isw 例程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "isw"
  - "is"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "is 例程"
  - "isw 例程"
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is、isw 例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

|||  
|-|-|  
|[isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|  
|[isalpha、iswalpha、\_isalpha\_l、\_iswalpha\_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|  
|[isascii，\_\_isascii、 iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|  
|[isblank、iswblank、\_isblank\_l、\_iswblank\_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint、iswprint、\_isprint\_l、\_iswprint\_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|  
|[iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|  
|[\_isctype、iswctype、\_isctype\_l、\_iswctype\_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper、\_isupper\_l、iswupper、\_iswupper\_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|  
|[isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|  
  
## 备注  
 这些实例测试指定条件的字符。  
  
 **is** 实例产生从– 1 到 **UCHAR\_MAX** \(0xFF\)，包含，所有整数参数的有意义的结果 \(`EOF`\)。  期望自变量类型为 `int`。  
  
> [!CAUTION]
>  对于以 **is** 的实例，传递类型为 `char` 的参数可能产生不可预知的结果。  一个类型为 `char` 的 SBCS 或 MBCS 单字节字符的值大于 0x7F，则该值为负值。  如果传递了一个 `char`，则编译器可能将该值转换为一个有符号的 `int` 或一个有符号的  **long**。  编译器可能对该值进行符号扩展，从而产生意外的结果。  
  
 **isw** 实例产生从– 1 到 \(**WEOF**\) 到 0xFFFF，包含，所有整数值的有意义的结果。  **wint\_t** 数据类型作在 WCHAR.H 定义为 **unsigned short**;它可以表示任何宽字符或宽字符文件结尾 \(**WEOF**\) 的值。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 **\_l** 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 **\_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
 在“C”区域设置，**is** 实例的测试条件如下所示：  
  
 `isalnum`  
 字母数字 \(A – Z, a – z,或 0 – 9\)。  
  
 `isalpha`  
 按字母 \(A – Z 或 a – z\)。  
  
 `__isascii`  
 ASCII 字符 \(0x00 – 0x7F\)。  
  
 `isblank`  
 水平制表符或空格字符 \(0x09 或 0x20\)。  
  
 `iscntrl`  
 控制字符 \(0x00 – 0x1F 或 0x7F\)。  
  
 `__iscsym`  
 字母、下划线或数字。  
  
 `__iscsymf`  
 字母或下划线。  
  
 **isdigit**  
 十进制数字 \(0 – 9\)。  
  
 `isgraph`  
 可打印字符除空格 \( \)。  
  
 `islower`  
 小写字母 \(a – z\)。  
  
 `isprint`  
 可打印字符包括空格 \(0x20 – 0x7E\)。  
  
 `ispunct`  
 标点字符。  
  
 `isspace`  
 空格字符 \(0x09 – 0x0D 或 0x20\)。  
  
 `isupper`  
 大写字母 \(A – Z\)。  
  
 `isxdigit`  
 十六进制数字 \(A\-F，a\-f 或 0 – 9\)。  
  
 对于 **isw** 实例，指定的条件的测试的结果与区域设置无关。  **isw** 函数的测试条件如下所示：  
  
 `iswalnum`  
 `iswalpha`或 `iswdigit`。  
  
 `iswalpha`  
 任何实现定义的宽字符设置那些 `iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 都不是非零。  `iswalpha` 仅返回 `iswupper` 或 `iswlower` 的非零的宽字符的非零值。  
  
 `iswascii`  
 宽字符代表ASCII 字符 \(0x0000 – 0x007F\) 。  
  
 `iswblank`  
 对应于标准的空格字符或者是一个实现定义的一组宽字符的 `iswalnum` 是错误的宽字符。  标准空白符是空格 \(L“\) 和水平制表符 \(L”\\t”\)。  
  
 `iswcntrl`  
 控件宽字符。  
  
 **\_\_iswcsym**  
 **isalnum** 的任何宽字符或“\_”字符是真的。  
  
 **\_\_iswcsymf**  
 `iswalpha` 的任何宽字符或“\_”字符是真的。  
  
 `iswctype`  
 字符具有 `desc` 参数特定的属性。  `iswctype`的 `desc` 参数的每个有效值，有等效的宽字符类别的实例，如下表所示：  
  
 **Equivalence of iswctype\(**   
 ***c, desc* \) to Other isw Testing Routines**  
  
|*desc* 参数的值|iswctype \( *c，desc* \) 等效值|  
|-----------------|---------------------------------|  
|**\_ALPHA**|**iswalpha\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_DIGIT**|**iswalnum\(** `c` **\)**|  
|**\_BLANK**|**iswblank\(** `c` **\)**|  
|**\_CONTROL**|**iswcntrl\(** `c` **\)**|  
|**\_DIGIT**|**iswdigit\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_DIGIT** &#124; **\_PUNCT**|**iswgraph\(** `c` **\)**|  
|**\_LOWER**|**iswlower\(** `c` **\)**|  
|**\_ALPHA** &#124; **\_BLANK** &#124; **\_DIGIT** &#124; **\_PUNCT**|**iswprint\(** `c` **\)**|  
|**\_PUNCT**|**iswpunct\(** `c` **\)**|  
|**\_BLANK**|**iswblank\(** `c` **\)**|  
|**\_SPACE**|**iswspace\(** `c` **\)**|  
|**\_UPPER**|**iswupper\(** `c` **\)**|  
|**\_HEX**|**iswxdigit\(** `c` **\)**|  
  
 `iswdigit`  
 宽字符相对应与十进制数字字符。  
  
 `iswgraph`  
 可打印宽字符除空格宽字符 \(L“\)。  
  
 `iswlower`  
 小写字母或一个实现定义 `iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 都不是非零的设置宽字符。  `iswlower` 仅返回非零对应于小写字母的宽字符。  
  
 `iswprint`  
 可打印宽字符，包括空格宽字符 \(L“\)。  
  
 `iswpunct`  
 `iswalnum` 中既不是空格宽字符 \(L“\) 也不是宽字符的打印宽字符是非零。  
  
 `iswspace`  
 对应于标准的空格字符或者是一个实现定义的一组宽字符的 `iswalnum` 是错误的宽字符。  标准的空白字符：空格（L' '），换页（L'\\f'），换行（L'\\n'），回车（L'\\r'），水平制表符（L'\\t'），并垂直制表符（L'\\v'）。  
  
 `iswupper`  
 `iswcntrl`、`iswdigit`、`iswpunct`或 `iswspace` 其中的大写字符或是实现定义集合的宽字符都不是非零的宽字符。  `iswupper` 仅返回非零对应于大写字符的宽字符。  
  
 `iswxdigit`  
 对应于十六进制数字字符的宽字符。  
  
## 示例  
  
```  
// crt_isfam.c  
/* This program tests all characters between 0x0  
 * and 0x7F, then displays each character with abbreviations  
 * for the character-type codes that apply.  
 */  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   for( ch = 0; ch <= 0x7F; ch++ )  
   {  
      printf( "%.2x  ", ch );  
      printf( " %c", isprint( ch )  ? ch   : ' ' );  
      printf( "%4s", isalnum( ch )  ? "AN" : "" );  
      printf( "%3s", isalpha( ch )  ? "A"  : "" );  
      printf( "%3s", __isascii( ch )  ? "AS" : "" );  
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );  
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );  
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );  
      printf( "%3s", isdigit( ch )  ? "D"  : "" );  
      printf( "%3s", isgraph( ch )  ? "G"  : "" );  
      printf( "%3s", islower( ch )  ? "L"  : "" );  
      printf( "%3s", ispunct( ch )  ? "PU" : "" );  
      printf( "%3s", isspace( ch )  ? "S"  : "" );  
      printf( "%3s", isprint( ch )  ? "PR" : "" );  
      printf( "%3s", isupper( ch )  ? "U"  : "" );  
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );  
      printf( ".\n" );  
   }  
}  
```  
  
## Output  
  
```  
00            AS  C                              .  
01            AS  C                              .  
02            AS  C                              .  
03            AS  C                              .  
04            AS  C                              .  
05            AS  C                              .  
06            AS  C                              .  
07            AS  C                              .  
08            AS  C                              .  
09            AS  C                    S         .  
0a            AS  C                    S         .  
0b            AS  C                    S         .  
0c            AS  C                    S         .  
0d            AS  C                    S         .  
0e            AS  C                              .  
0f            AS  C                              .  
10            AS  C                              .  
11            AS  C                              .  
12            AS  C                              .  
13            AS  C                              .  
14            AS  C                              .  
15            AS  C                              .  
16            AS  C                              .  
17            AS  C                              .  
18            AS  C                              .  
19            AS  C                              .  
1a            AS  C                              .  
1b            AS  C                              .  
1c            AS  C                              .  
1d            AS  C                              .  
1e            AS  C                              .  
1f            AS  C                              .  
20            AS                       S PR      .  
21   !        AS              G    PU    PR      .  
22   "        AS              G    PU    PR      .  
23   #        AS              G    PU    PR      .  
24   $        AS              G    PU    PR      .  
25   %        AS              G    PU    PR      .  
26   &        AS              G    PU    PR      .  
27   '        AS              G    PU    PR      .  
28   (        AS              G    PU    PR      .  
29   )        AS              G    PU    PR      .  
2a   *        AS              G    PU    PR      .  
2b   +        AS              G    PU    PR      .  
2c   ,        AS              G    PU    PR      .  
2d   -        AS              G    PU    PR      .  
2e   .        AS              G    PU    PR      .  
2f   /        AS              G    PU    PR      .  
30   0  AN    AS   CS      D  G          PR     X.  
31   1  AN    AS   CS      D  G          PR     X.  
32   2  AN    AS   CS      D  G          PR     X.  
33   3  AN    AS   CS      D  G          PR     X.  
34   4  AN    AS   CS      D  G          PR     X.  
35   5  AN    AS   CS      D  G          PR     X.  
36   6  AN    AS   CS      D  G          PR     X.  
37   7  AN    AS   CS      D  G          PR     X.  
38   8  AN    AS   CS      D  G          PR     X.  
39   9  AN    AS   CS      D  G          PR     X.  
3a   :        AS              G    PU    PR      .  
3b   ;        AS              G    PU    PR      .  
3c   <        AS              G    PU    PR      .  
3d   =        AS              G    PU    PR      .  
3e   >        AS              G    PU    PR      .  
3f   ?        AS              G    PU    PR      .  
40   @        AS              G    PU    PR      .  
41   A  AN  A AS   CS CSF     G          PR  U  X.  
42   B  AN  A AS   CS CSF     G          PR  U  X.  
43   C  AN  A AS   CS CSF     G          PR  U  X.  
44   D  AN  A AS   CS CSF     G          PR  U  X.  
45   E  AN  A AS   CS CSF     G          PR  U  X.  
46   F  AN  A AS   CS CSF     G          PR  U  X.  
47   G  AN  A AS   CS CSF     G          PR  U   .  
48   H  AN  A AS   CS CSF     G          PR  U   .  
49   I  AN  A AS   CS CSF     G          PR  U   .  
4a   J  AN  A AS   CS CSF     G          PR  U   .  
4b   K  AN  A AS   CS CSF     G          PR  U   .  
4c   L  AN  A AS   CS CSF     G          PR  U   .  
4d   M  AN  A AS   CS CSF     G          PR  U   .  
4e   N  AN  A AS   CS CSF     G          PR  U   .  
4f   O  AN  A AS   CS CSF     G          PR  U   .  
50   P  AN  A AS   CS CSF     G          PR  U   .  
51   Q  AN  A AS   CS CSF     G          PR  U   .  
52   R  AN  A AS   CS CSF     G          PR  U   .  
53   S  AN  A AS   CS CSF     G          PR  U   .  
54   T  AN  A AS   CS CSF     G          PR  U   .  
55   U  AN  A AS   CS CSF     G          PR  U   .  
56   V  AN  A AS   CS CSF     G          PR  U   .  
57   W  AN  A AS   CS CSF     G          PR  U   .  
58   X  AN  A AS   CS CSF     G          PR  U   .  
59   Y  AN  A AS   CS CSF     G          PR  U   .  
5a   Z  AN  A AS   CS CSF     G          PR  U   .  
5b   [        AS              G    PU    PR      .  
5c   \        AS              G    PU    PR      .  
5d   ]        AS              G    PU    PR      .  
5e   ^        AS              G    PU    PR      .  
5f   _        AS   CS CSF     G    PU    PR      .  
60   `        AS              G    PU    PR      .  
61   a  AN  A AS   CS CSF     G  L       PR     X.  
62   b  AN  A AS   CS CSF     G  L       PR     X.  
63   c  AN  A AS   CS CSF     G  L       PR     X.  
64   d  AN  A AS   CS CSF     G  L       PR     X.  
65   e  AN  A AS   CS CSF     G  L       PR     X.  
66   f  AN  A AS   CS CSF     G  L       PR     X.  
67   g  AN  A AS   CS CSF     G  L       PR      .  
68   h  AN  A AS   CS CSF     G  L       PR      .  
69   i  AN  A AS   CS CSF     G  L       PR      .  
6a   j  AN  A AS   CS CSF     G  L       PR      .  
6b   k  AN  A AS   CS CSF     G  L       PR      .  
6c   l  AN  A AS   CS CSF     G  L       PR      .  
6d   m  AN  A AS   CS CSF     G  L       PR      .  
6e   n  AN  A AS   CS CSF     G  L       PR      .  
6f   o  AN  A AS   CS CSF     G  L       PR      .  
70   p  AN  A AS   CS CSF     G  L       PR      .  
71   q  AN  A AS   CS CSF     G  L       PR      .  
72   r  AN  A AS   CS CSF     G  L       PR      .  
73   s  AN  A AS   CS CSF     G  L       PR      .  
74   t  AN  A AS   CS CSF     G  L       PR      .  
75   u  AN  A AS   CS CSF     G  L       PR      .  
76   v  AN  A AS   CS CSF     G  L       PR      .  
77   w  AN  A AS   CS CSF     G  L       PR      .  
78   x  AN  A AS   CS CSF     G  L       PR      .  
79   y  AN  A AS   CS CSF     G  L       PR      .  
7a   z  AN  A AS   CS CSF     G  L       PR      .  
7b   {        AS              G    PU    PR      .  
7c   |        AS              G    PU    PR      .  
7d   }        AS              G    PU    PR      .  
7e   ~        AS              G    PU    PR      .  
7f            AS  C                              .  
```  
  
## 请参阅  
 [字符分类](../c-runtime-library/character-classification.md)   
 [区域设置](../c-runtime-library/locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [多字节字符序列的解释](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [to 函数](../c-runtime-library/to-functions.md)