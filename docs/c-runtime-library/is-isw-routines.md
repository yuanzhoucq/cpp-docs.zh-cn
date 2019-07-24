---
title: is、isw 例程
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: 1550f8f012802e03e9228e67c381915b1b4e1d64
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376032"
---
# <a name="is-isw-routines"></a>is、isw 例程

|||
|-|-|
|[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|
|[iscsym、iscsymf、__iscsym、\___iswcsym、\___iscsymf、\___iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper、_isupper_l、iswupper、_iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|

## <a name="remarks"></a>备注

特定条件下的例程测试字符。

对于从 -1 (`EOF`) 到 **UCHAR_MAX** (0xFF)（含）的任何整数参数，**is** 例程都将产生有意义的结果。 参数类型应为 `int`。

> [!CAUTION]
> 对于 **is** 例程，传递 `char` 参数类型可能会产生不可预测的结果。 如果类型为 `char` 的 SBCS 或 MBCS 单字节字符的值大于 0x7F，则该值为负值。 如果传递了 `char`，编译器可能会将该值转换为带符号的 `int` 或带符号的 **long**。 该值可能由编译器进行符号扩展，产生意外的结果。

对于从 -1 (**WEOF**) 到 0xFFFF（含）的任何整数值，**isw** 例程都会产生有意义的结果。 **wint_t** 数据类型在 WCHAR.H 中定义为 **unsigned short**；它可以保存任何宽字符或宽字符文件尾 (**WEOF**) 值。

输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。

在“C”区域设置中，**is** 例程的测试条件如下所示：

`isalnum`<br/>
字母数字（A - Z、a-z 或 0-9）。

`isalpha`<br/>
字母（A - Z 或 a - z）。

`__isascii`<br/>
ASCII 字符 (0x00 - 0x7F)。

`isblank`<br/>
水平制表符或空格字符（0x09 或 0x20）。

`iscntrl`<br/>
控制字符（0x00-0x1F 或 0x7F）。

`__iscsym`<br/>
字母、下划线或数字。

`__iscsymf`<br/>
字母或下划线。

`isdigit`<br/>
十进制数字 (0 - 9)。

`isgraph`<br/>
除空格 ( ) 之外的可打印字符。

`islower`<br/>
小写字母 (a - z)。

`isprint`<br/>
包括空格的可打印字符 (0x20 - 0x7E)。

`ispunct`<br/>
标点字符。

`isspace`<br/>
空白字符（0x09-0x0D 或 0x20）。

`isupper`<br/>
大写字母 (A - Z)。

`isxdigit`<br/>
十六进制数字（A-F、a-f 或 0-9）。

对于 **isw** 例程，指定条件的测试结果与区域设置无关。 **isw** 函数的测试条件如下所示：

`iswalnum`<br/>
`iswalpha` 或 `iswdigit`。

`iswalpha`<br/>
属于其中一个实现定义的集合（其中 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 没有一个为非零）的任何宽字符。 `iswalpha` 仅针对 `iswupper` 或 `iswlower` 为非零的宽字符返回非零。

`iswascii`<br/>
ASCII 字符 (0x0000-0x007F) 的宽字符表示形式。

`iswblank`<br/>
对应于标准空格字符，或是实现定义的宽字符集（其中 `iswalnum` 为 false）之一的宽字符。 标准空白字符是空格 (L' ') 和水平制表符 (L'\t')。

`iswcntrl`<br/>
控制宽字符。

`__iswcsym`<br/>
`isalnum` 为 true 的任何宽字符，或“_”字符。

`__iswcsymf`<br/>
`iswalpha` 为 true 的任何宽字符，或“_”字符。

`iswctype`<br/>
字符的属性由 `desc` 参数指定。 `iswctype` 的 `desc` 参数的每个有效值都有一个等效的宽字符分类例程，如下表所示：

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>iswctype(c, desc) 与其他 isw 测试例程的等效性

|*desc* 参数的值|iswctype( *c, desc* ) 等效项|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_CONTROL**|**iswcntrl(** `c` **)**|
|**_DIGIT**|**iswdigit(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph(** `c` **)**|
|**_LOWER**|**iswlower(** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint(** `c` **)**|
|**_PUNCT**|**iswpunct(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_SPACE**|**iswspace(** `c` **)**|
|**_UPPER**|**iswupper(** `c` **)**|
|**_HEX**|**iswxdigit(** `c` **)**|

`iswdigit`<br/>
对应于十进制数字字符的宽字符。

`iswgraph`<br/>
除了空格宽字符 (L' ') 之外的可打印宽字符。

`iswlower`<br/>
小写字母，或 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 没有一个为非零的其中一个实现定义的宽字符集。 `iswlower` 仅对与小写字母对应的宽字符返回非零值。

`iswprint`<br/>
包含空格宽字符 (L' ') 的可打印宽字符。

`iswpunct`<br/>
既不是空格宽字符 (L' ') 也不是 `iswalnum` 为非零值的宽字符的可打印宽字符。

`iswspace`<br/>
对应于标准空白字符，或是实现定义的宽字符集（其中 `iswalnum` 为 false）之一的宽字符。 标准空白字符是：空格 (L' ')、换页符 (L'\f')、换行符 (L'\n')、回车符 (L'\r')、水平制表符 (L'\t') 和垂直制表符 (L'\v')。

`iswupper`<br/>
宽字符是一个大写字母，或是 `iswcntrl`、`iswdigit`、`iswpunct` 或 `iswspace` 没有一个为非零的其中一个实现定义的宽字符集。 `iswupper` 仅对与大写字母对应的宽字符返回非零值。

`iswxdigit`<br/>
对应于十六进制数字字符的宽字符。

## <a name="example"></a>示例

```C
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

## <a name="output"></a>Output

```Output
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

## <a name="see-also"></a>请参阅

[字符分类](../c-runtime-library/character-classification.md)<br/>
[区域设置](../c-runtime-library/locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[多字节字符序列的解释](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to 函数](../c-runtime-library/to-functions.md)
