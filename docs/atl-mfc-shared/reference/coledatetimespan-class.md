---
title: "COleDateTimeSpan 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4091ca2c766d56d8398119413778af0a0405b8ab
ms.lasthandoff: 02/24/2017

---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 类
表示相对时间，时间跨度。  
  
## <a name="syntax"></a>语法  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|构造 `COleDateTimeSpan` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|生成带格式的字符串表示形式`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::GetDays](#getdays)|返回范围的日部分此`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetHours](#gethours)|返回范围的小时部分此`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|返回范围的分钟部分此`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|返回范围的第二个部分此`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetStatus](#getstatus)|获取此的状态 （有效期）`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|这将返回的天数`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|这将返回的小时数`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|这将返回的分钟数`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|这将返回的秒数`COleDateTimeSpan`对象表示。|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|设置此值`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::SetStatus](#setstatus)|设置的状态 （有效期） 这`COleDateTimeSpan`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|||  
|-|-|  
|[运算符 +、-](#operator_add_-)|添加、 减法运算，并将更改用于符号`COleDateTimeSpan`值。|  
|[运算符 + =、 =](#operator_add_eq_-_eq)|加法和减法`COleDateTimeSpan`从此值`COleDateTimeSpan`值。|  
|[运算符 =](#operator_eq)|副本`COleDateTimeSpan`值。|  
|[运算符 = =、<,></,><>](#coledatetimespan_relational_operators)|比较两个`COleDateTimeSpan`值。|  
|[运算符 double](#operator_double)|将此转换`COleDateTimeSpan`值赋给**double**。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|包含基础**double**此`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::m_status](#m_status)|包含此状态`COleDateTimeSpan`对象。|  
  
## <a name="remarks"></a>备注  
 `COleDateTimeSpan`没有基类的类。  
  
 一个`COleDateTimeSpan`保留以天为单位的时间。  
  
 `COleDateTimeSpan`适用于其伴生类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封装**日期**OLE 自动化的数据类型。 `COleDateTime`表示绝对时间值。 所有`COleDateTime`计算是涉及`COleDateTimeSpan`值。 这些类之间的关系相当于间的一个[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 有关详细信息`COleDateTime`和`COleDateTimeSpan`类，请参阅文章[日期和时间︰ 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 关系运算符  
 比较运算符。  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>参数  
 *dateSpan*  
 要比较的 `COleDateTimeSpan`。  
  
### <a name="return-value"></a>返回值  
 这些运算符比较两个日期/时间跨度值，并返回**true**如果条件为 true; 否则为**false**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果其中一个操作数无效，将发生 ATLASSERT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&25;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&26;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
 构造 `COleDateTimeSpan` 对象。  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>参数  
 `dblSpanSrc`  
 若要复制到新的天数`COleDateTimeSpan`对象。  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 指示要复制到新的日期和时间值`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 所有这些构造函数创建新`COleDateTimeSpan`对象初始化为指定的值。 这些构造函数的简要说明如下所示︰  
  
- **COleDateTimeSpan （)**构造`COleDateTimeSpan`对象初始化为 0。  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)**构造`COleDateTimeSpan`从浮点值的对象。  
  
- **COleDateTimeSpan (** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **)**构造`COleDateTimeSpan`对象初始化为指定的数字值。  
  
 新的状态`COleDateTimeSpan`对象设置为有效。  
  
 有关更多信息的边界`COleDateTimeSpan`值，请参阅文章[日期和时间︰ 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&14;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 生成带格式的字符串表示形式`COleDateTimeSpan`对象。  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>参数  
 `pFormat`  
 格式设置字符串类似于`printf`格式设置字符串。 格式设置代码，前面带有百分比 ( `%`) 登录，替换为相应`COleDateTimeSpan`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 值和含义的格式设置代码**格式**如下所示︰  
  
- **%H**中当前的一天  
  
- **%M**当前小时内的分钟数  
  
- **%S**中当前分钟秒数  
  
- **%%**百分号  
  
 上面列出的四个格式代码是格式将接受的唯一代码。  
  
-  
  
 `nID`  
 格式控件字符串资源 ID。  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含带格式的日期/时间范围值。  
  
### <a name="remarks"></a>备注  
 调用这些函数来创建时间跨度值的格式的表示。 如果此状态`COleDateTimeSpan`对象为 null，则返回值为空字符串。 如果状态为无效，则返回字符串将由字符串资源指定**IDS_INVALID_DATETIMESPAN**。  
  
 此函数的窗体的简要说明如下所示︰  
  
 **Format(** `pFormat` **)**  
 此窗体设置使用的格式字符串，包含前面以百分号 （%） 的特殊格式代码值的格式如下所示`printf`。 格式设置字符串作为参数传递给函数。  
  
 **Format(** `nID` **)**  
 此窗体设置使用的格式字符串，包含前面以百分号 （%） 的特殊格式代码值的格式如下所示`printf`。 格式设置字符串是一个资源。 该字符串资源的 ID 作为参数进行传递。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&15;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 检索此日期/时间范围值的日部分。  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值的日部分。  
  
### <a name="remarks"></a>备注  
 返回值之间这个函数范围内大约 – 3,615,000 和 3,615,000。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&16;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 检索此日期/时间范围值的小时部分。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值的小时部分。  
  
### <a name="remarks"></a>备注  
 通过此函数范围-23 到 23 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&17;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 检索此日期/时间范围值的分钟部分。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值的分钟部分。  
  
### <a name="remarks"></a>备注  
 通过此函数范围-59 到 59 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&18;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 检索此日期/时间范围值的第二个部分。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值的秒部分。  
  
### <a name="remarks"></a>备注  
 通过此函数范围-59 到 59 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&19;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 获取此的状态 （有效期）`COleDateTimeSpan`对象。  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此状态`COleDateTimeSpan`值。  
  
### <a name="remarks"></a>备注  
 返回值由**DateTimeSpanStatus**枚举类型，在其中定义`COleDateTimeSpan`类。  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 有关这些状态值的简要说明，请参阅下面的列表︰  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 也就是说，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，即，已为此对象中提供任何值。 (这是"null"数据库意义上的"having 没有值，"，而不 c + + **NULL**。)  
  
 状态`COleDateTimeSpan`对象是在以下情况下无效︰  
  
-   如果此对象已出现溢出或下溢在过程中遇到算术赋值运算，也就是说，`+=`或`-=`。  
  
-   如果无效的值分配给此对象。  
  
-   如果已显式设置此对象的状态为无效的使用`SetStatus`。  
  
 有关可能会将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
 有关更多信息的边界`COleDateTimeSpan`值，请参阅文章[日期和时间︰ 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 检索此以天数表示的日期/时间范围值。  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>返回值  
 以天为单位表示此日期/时间范围值。 虽然此函数原型是返回一个双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 通过此函数范围大约 – 3.65e6 和 3.65e6 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&20;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 检索此日期/时间跨度值，以小时为单位。  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值，以小时为单位。 虽然此函数原型是返回一个双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 通过此函数范围大约 – 8.77e7 和 8.77e7 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 检索此以分钟为单位表示的日期/时间范围值。  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 以分钟为单位表示此日期/时间范围值。 虽然此函数原型是返回一个双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 通过此函数范围大约 – 5.26e9 和 5.26e9 之间的返回值。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 检索此日期/时间范围值以秒为单位。  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值，以秒为单位。 虽然此函数原型是返回一个双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 此函数的返回值之间的范围大约 – 3.16e11 到 3.16e11。  
  
 其他查询的值的函数的`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="m_span"></a>COleDateTimeSpan::m_span  
 基础**double**值这`COleDateTime`对象。  
  
```
double m_span;
```  
  
### <a name="remarks"></a>备注  
 此值表示日期/时间范围以天为单位。  
  
> [!CAUTION]
>  更改中的值**double**数据成员将此值更改`COleDateTimeSpan`对象。 不会更改此状态`COleDateTimeSpan`对象。  
  
##  <a name="m_status"></a>COleDateTimeSpan::m_status  
 此数据成员的类型是枚举的类型**DateTimeSpanStatus**，其定义内`COleDateTimeSpan`类。  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>备注  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 有关这些状态值的简要说明，请参阅下面的列表︰  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 也就是说，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，即，已为此对象中提供任何值。 (这是"null"数据库意义上的"having 没有值，"，而不 c + + **NULL**。)  
  
 状态`COleDateTimeSpan`对象是在以下情况下无效︰  
  
-   如果此对象已出现溢出或下溢在过程中遇到算术赋值运算，也就是说，`+=`或`-=`。  
  
-   如果无效的值分配给此对象。  
  
-   如果已显式设置此对象的状态为无效的使用[SetStatus](#setstatus)。  
  
 有关可能会将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
> [!CAUTION]
>  此数据成员是针对高级编程情况。 应使用内联成员函数[GetStatus](#getstatus)和[SetStatus](#setstatus)。 请参阅`SetStatus`有关显式设置此数据成员的其他注意事项。  
  
 有关更多信息的边界`COleDateTimeSpan`值，请参阅文章[日期和时间︰ 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 副本`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>备注  
 此重载的赋值运算符将源日期/时间范围值复制到此`COleDateTimeSpan`对象。  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +、-  
 添加、 减法运算，并将更改用于符号`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>备注  
 前两个运算符，您将添加并将日期/时间范围值相减。 第三个可让您更改日期/时间范围值的符号。  
  
 如果任一操作数是 null，所生成的状态`COleDateTimeSpan`值为 null。  
  
 如果任一操作数无效，且另一个则不为 null，所生成的状态`COleDateTimeSpan`值无效。  
  
 有关有效、 无效的并且为 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities 第&23;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator + =、 =  
 加法和减法`COleDateTimeSpan`从此值`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>备注  
 这些运算符，您将添加并将从该日期/时间范围值相减`COleDateTimeSpan`对象。 如果任一操作数是 null，所生成的状态`COleDateTimeSpan`值为 null。  
  
 如果任一操作数无效，且另一个则不为 null，所生成的状态`COleDateTimeSpan`值无效。  
  
 有关有效、 无效的并且为 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&24;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>COleDateTimeSpan::operator double  
 将此转换`COleDateTimeSpan`值赋给**double**。  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>备注  
 此运算符将返回此值`COleDateTimeSpan`天的浮点数形式的值。  
  
##  <a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 设置此日期/时间范围值的值。  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 指示要复制到此日期范围内与时间跨度值`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 对于查询的值的函数`COleDateTimeSpan`对象，请参阅下面的成员函数︰  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&21;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 设置的状态 （有效期） 这`COleDateTimeSpan`对象。  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>参数  
 *status*  
 为此新的状态值`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 *状态*参数的值由定义**DateTimeSpanStatus**枚举类型，在其中定义`COleDateTimeSpan`类。  
  
 `enum DateTimeSpanStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 有关这些状态值的简要说明，请参阅下面的列表︰  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 也就是说，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，即，已为此对象中提供任何值。 (这是"null"数据库意义上的"having 没有值，"，而不 c + + **NULL**。)  
  
    > [!CAUTION]
    >  此函数是针对高级编程情况。 此函数不会更改此对象中的数据。 它通常用于在将状态设置为`null`或**无效**。 请注意，赋值运算符 ([运算符 =](#eq)) 和[SetDateTimeSpan](#setdatetimespan)不要将基于源值的对象的状态设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities #&22;](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime 类](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)



