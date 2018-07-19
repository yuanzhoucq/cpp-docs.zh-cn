---
title: CTimeSpan 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30b110e9c9f737f8dbbe46782613ca80240fb943
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880425"
---
# <a name="ctimespan-class"></a>CTimeSpan 类
长时间，在内部存储为中的时间跨度的秒数。  
  
## <a name="syntax"></a>语法  
  
```
class CTimeSpan
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTimeSpan::CTimeSpan](#ctimespan)|构造`CTimeSpan`以各种方式的对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTimeSpan::Format](#format)|将转换`CTimeSpan`到带格式字符串。|  
|[CTimeSpan::GetDays](#getdays)|返回一个值，表示在此完整天数`CTimeSpan`。|  
|[CTimeSpan::GetHours](#gethours)|返回一个值，表示当前日期 (为-23 到 23) 中的小时数。|  
|[CTimeSpan::GetMinutes](#getminutes)|返回一个值，表示当前的小时 (-59 到 59) 中的分钟数。|  
|[CTimeSpan::GetSeconds](#getseconds)|返回一个值，表示当前分钟 (-59 到 59) 中的秒数。|  
|[CTimeSpan::GetTimeSpan](#gettimespan)|返回的值`CTimeSpan`对象。|  
|[CTimeSpan::GetTotalHours](#gettotalhours)|返回一个值，表示在此完整小时总数`CTimeSpan`。|  
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|返回一个值，表示在此完整分钟总数`CTimeSpan`。|  
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|返回一个值，表示在此完整秒为单位的总数`CTimeSpan`。|  
|[CTimeSpan::Serialize64](#serialize64)|序列化或从存档的数据。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 +-](#operator_add_-)|将添加并减去`CTimeSpan`对象。|  
|[operator + = =](#operator_add_eq_-_eq)|将添加并减去`CTimeSpan`对象与此`CTimeSpan`。|  
|[运算符 = = < 等。](#ctimespan_comparison_operators)|比较两个相对时间值。|  
  
## <a name="remarks"></a>备注  
 `CTimeSpan` 没有基类。  
  
 `CTimeSpan` 函数将转换为各种组合的天数、 小时、 分钟、 秒和秒。  
  
 `CTimeSpan`对象存储在 **__time64_t**结构，它是 8 个字节。  
  
 伴生类， [CTime](../../atl-mfc-shared/reference/ctime-class.md)，表示一个绝对时间。  
  
 `CTime`和`CTimeSpan`类并不设计用于派生。 因为没有虚拟函数，这两者的大小`CTime`和`CTimeSpan`对象是完全 8 个字节。 大多数成员函数是内联。  
  
 有关使用的详细信息`CTimeSpan`，请参阅文章[日期和时间](../../atl-mfc-shared/date-and-time.md)，和[时间管理](../../c-runtime-library/time-management.md)中*运行时库参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atltime.h  
  
##  <a name="ctimespan_comparison_operators"></a>  CTimeSpan 比较运算符  
 比较运算符。  
  
```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 *s p a n*  
  
 要比较的对象。  
  
### <a name="return-value"></a>返回值  
 这些运算符比较两个相对时间值。 它们返回 TRUE，如果条件为 true;否则为 FALSE。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]  
  
##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan  
 构造`CTimeSpan`以各种方式的对象。  
  
```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(  
 LONG lDays,
 int nHours,
 int nMins,
 int nSecs) throw();
```  
  
### <a name="parameters"></a>参数  
 *timeSpanSrc*  
 一个`CTimeSpan`已存在的对象。  
  
 *time*  
 一个 **__time64_t**时间值，该值是在时间跨度的秒数。  
  
 *lDays*， *n 小时*， *nMins*， *nSecs*  
 天、 小时、 分钟和秒，分别。  
  
### <a name="remarks"></a>备注  
 所有这些构造函数创建一个新`CTimeSpan`初始化使用指定的相对时间对象。 下面描述了每个构造函数：  
  
- `CTimeSpan( );` 构造未初始化`CTimeSpan`对象。  
  
- `CTimeSpan( const CTimeSpan& );` 构造`CTimeSpan`从另一个对象`CTimeSpan`值。  
  
- `CTimeSpan( __time64_t );` 构造`CTimeSpan`对象从 **__time64_t**类型。  
  
- `CTimeSpan( LONG, int, int, int );` 构造`CTimeSpan`从每个组件的组件的对象限制为以下范围：  
  
    |组件|范围|  
    |---------------|-----------|  
    |*lDays*|0-25,000 （近似）|  
    |*n 小时*|0-23|  
    |*nMins*|0-59|  
    |*nSecs*|0-59|  
  
 请注意，Microsoft 基础类库的调试版本断言，如果一个或多个时间组件不在范围。 它由你负责验证之前调用的参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]  
  
##  <a name="format"></a>  CTimeSpan::Format  
 生成对应于此的格式化的字符串`CTimeSpan`。  
  
```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>参数  
 *pFormat*， *pszFormat*  
 格式设置字符串类似于`printf`格式设置字符串。 格式设置代码，前面有百分比 (`%`) 登录，将替换为相应`CTimeSpan`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 值和格式设置代码的含义`Format`如下所示：  
  
- **%D**总在此天数 `CTimeSpan`  
  
- **%H**当前天的小时  
  
- **%M**内当前小时的分钟数  
  
- **%S**当前分钟的秒  
  
- **%%** 百分比符号  
  
 *nID*  
 用于标识此格式的字符串的 ID。  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含格式的时间。  
  
### <a name="remarks"></a>备注  
 在库的调试版本检查的格式设置代码和断言的代码不在上面的列表。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]  
  
##  <a name="getdays"></a>  CTimeSpan::GetDays  
 返回一个值，表示在此完整天数`CTimeSpan`。  
  
```
LONGLONG GetDays() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回在时间跨度内完成 24 小时制数。 此值可为负数，如果时间跨度为负。  
  
### <a name="remarks"></a>备注  
 请注意，可能会导致夏时制`GetDays`以返回可能令人惊讶的结果。 例如，当 DST 时生效，`GetDays`报告为 29，不是 30，4 月 1 日至 5 月 1 天之间的数，因为年 4 月中的一天缩短晚一小时，因此不能算作完成一天。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]  
  
##  <a name="gethours"></a>  CTimeSpan::GetHours  
 返回一个值，表示当前日期 (为-23 到 23) 中的小时数。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回当前日期中的小时数。 范围为-23 到 23。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]  
  
##  <a name="getminutes"></a>  CTimeSpan::GetMinutes  
 返回一个值，表示当前的小时 (-59 到 59) 中的分钟数。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回在当前小时的分钟数。 范围是-59 到 59。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[GetHours](#gethours)。  
  
##  <a name="getseconds"></a>  CTimeSpan::GetSeconds  
 返回一个值，表示当前分钟 (-59 到 59) 中的秒数。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回在当前分钟的秒数。 范围是-59 到 59。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[GetHours](#gethours)。  
  
##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan  
 返回的值`CTimeSpan`对象。  
  
```
__ time64_t GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回的当前值`CTimeSpan`对象。  
  
##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours  
 返回一个值，表示在此完整小时总数`CTimeSpan`。  
  
```
LONGLONG GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 在此返回的完整小时总数`CTimeSpan`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]  
  
##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes  
 返回一个值，表示在此完整分钟总数`CTimeSpan`。  
  
```
LONGLONG GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 在此返回完整的分钟总数`CTimeSpan`。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[GetTotalHours](#gettotalhours)。  
  
##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds  
 返回一个值，表示在此完整秒为单位的总数`CTimeSpan`。  
  
```
LONGLONG GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 在此返回总完成的秒数`CTimeSpan`。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[GetTotalHours](#gettotalhours)。  
  
##  <a name="operator_add_-"></a>  CTimeSpan::operator +、-  
 将添加并减去`CTimeSpan`对象。  
  
```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>参数  
 *s p a n*  
 要添加到值`CTimeSpan`对象。  
  
### <a name="return-value"></a>返回值  
 一个`CTimeSpan`对象，表示操作的结果。  
  
### <a name="remarks"></a>备注  
 这两个运算符允许您以，加法和减法`CTimeSpan`到和从每个其他对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator + =、 =  
 将添加并减去`CTimeSpan`对象与此`CTimeSpan`。  
  
```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>参数  
 *s p a n*  
 要添加到值`CTimeSpan`对象。  
  
### <a name="return-value"></a>返回值  
 已更新`CTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 这些运算符使您得以，加法和减法`CTimeSpan`对象与此`CTimeSpan`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]  
  
##  <a name="serialize64"></a>  CTimeSpan::Serialize64  
  
> [!NOTE]
>  此方法才在 MFC 项目中可用。  
  
 序列化到或从存档的成员变量与关联的数据。  
  
```
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 *ar*  
 `CArchive`你想要更新的对象。  
  
### <a name="return-value"></a>返回值  
 已更新`CArchive`对象。  
  
## <a name="see-also"></a>请参阅  
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)


