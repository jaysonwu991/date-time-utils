# date-time-utils

A Util Library For Date && Time Operations, it can be used in both CommonJS and ES Module, and it supports both JS and TS as well.

> Warning: This module won't check if the parameters are valid for you, and it won't throw any errors when using.

## Date Parsing Support

> Warning: Note that all date data is parsed by `new Date()`, be careful to the use cases with locale and timezone.

| Data Type |      Example Date Data       |
| :-------: | :--------------------------: |
|  string   |         '2020-02-01'         |
|  string   |         '2020/02/01'         |
|  string   |      '2020-02-01T10:45'      |
|  string   |    '2020-02-01T10:45:00'     |
|  string   |  '2020-02-01T10:45:00+0800'  |
|  string   |    '2020-02-01 05:20:00'     |
|  string   | '2020-02-01 05:20:00 +08:00' |
|  string   |  '2020-01-31T21:20:00.000Z'  |
|  number   |        1580515200000         |

# Usage

## Installation

```bash
$ npm i -S @jayson991/date-time-utils
```

## Use In CommonJS

```javascript
const { getWeek, getCalendar } = require('@jayson991/date-time-utils');

console.log(JSON.stringify(getCalendar('2020-02-01', '2020-02-03')));

console.log(getWeek('2020-02-01'));
console.log(getWeek('2020/02/01'));
console.log(getWeek(1580515200000));
```

### getCalendar Output

```json
[
  { "year": 2020, "month": 1, "day": 1, "week": 6 },
  { "year": 2020, "month": 1, "day": 2, "week": 0 },
  { "year": 2020, "month": 1, "day": 3, "week": 1 }
]
```

### getWeek Output

```javascript
6; // console.log(getWeek('2020-02-01'))
6; // console.log(getWeek('2020/02/01'))
6; // console.log(getWeek(1580515200000))
```

## Use In ES6 Module

```javascript
import { getCalendar, getWeek } from '@jayson991/date-time-utils';

console.log(JSON.stringify(getCalendar('2020-02-01', '2020-02-03')));

console.log(getWeek('2020-02-01'));
console.log(getWeek('2020/02/01'));
console.log(getWeek(1580515200000));
```

### getCalendar Output

```json
[
  { "year": 2020, "month": 1, "day": 1, "week": 6 },
  { "year": 2020, "month": 1, "day": 2, "week": 0 },
  { "year": 2020, "month": 1, "day": 3, "week": 1 }
]
```

### getWeek Output

```javascript
6; // console.log(getWeek('2020-02-01'))
6; // console.log(getWeek('2020/02/01'))
6; // console.log(getWeek(1580515200000))
```

# Explanation

| field |                 formation                  |
| :---: | :----------------------------------------: |
| month | 0 -> January, 1 -> February, 2 -> March... |
| week  | 0 -> Sunday, 1 -> Monday, 2 -> Tuesday...  |

# All Functions

> Please see more examples in [test](https://github.com/jaysonwu991/date-time-utils/blob/main/tests/index.spec.ts) file, for it is not just like the below provided.

> Including getCalendar & getWeek. getDays is for the day difference of two dates, getHours is for the hour difference of two dates, getMinutes is for the minute difference of two dates, getSeconds is for the second difference of two dates, these four functions can be combined together to get the difference of two dates.

|     Name     |                         Output Result                          |
| :----------: | :------------------------------------------------------------: |
|  addPrefix   |                      addPrefix(1) -> '01'                      |
| deletePrefix |                    deletePrefix('01') -> 1                     |
| getMonthWeek |              getMonthWeek('2020', '2', '7') -> 2               |
| getYearWeek  |              getYearWeek('2020', '2', '10') -> 7               |
|   getDays    |            getDays('2020-02-01', '2020-02-03') -> 2            |
|   getHours   |     getHours('2020-02-01T10:45', '2020-02-03T12:15') -> 1      |
|  getMinutes  |    getMinutes('2020-02-01T10:45', '2020-02-03T12:15') -> 30    |
|  getSeconds  | getSeconds('2020-02-01T10:45:20', '2020-02-03T12:15:50') -> 30 |
