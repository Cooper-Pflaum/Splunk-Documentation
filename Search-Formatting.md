






## Formatting Time To Make It Look Readable
---
-> *_time* is ugly (ex. 2023-12-13 16:48:13.554)\
-> Use the code below to format it into a more readable format (12-13-2023 4:48PM)
```
| convert timeformat="%m-%d-%Y %l:%M %p" ctime(_time) AS Time
| sort - _time
```

