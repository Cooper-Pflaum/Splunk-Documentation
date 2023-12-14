





# Time
### Formatting Time To A Human Format
- **_time** is ugly (ex. 2023-12-13 16:48:13.554)\
- This converts that into a more readable format (12-13-2023 4:48PM)
```
| convert timeformat="%m-%d-%Y %l:%M %p" ctime(_time) AS Time
```

### Sort by most recent first
```
| sort - _time
```

# Columns
### Renaming
- Rename the Column Titles by using the **rename** command
    NOTE: If you want multi-word names then include "" around your words
```
| rename deviceName AS "Device Name"
| rename eventData.ssid AS SSID
```
- You must use the new term for the rest of the search
```
| table "Device Name" SSID _time
```
