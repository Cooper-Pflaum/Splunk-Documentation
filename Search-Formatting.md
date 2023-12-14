





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
    NOTE: If you want multi-word names then include " " around your words
```
| rename deviceName AS "Device Name"
| rename eventData.ssid AS SSID
```
- You must use the new term for the rest of the search
```
| table "Device Name" SSID _time
```


# Searching
### Reformmating Search Results
- The best way to change results into a format that you want is to use the ```eval``` command
```
| eval EventCode=case(
    EventCode="4954", "Success",
    EventCode="6144", "Success",
    EventCode="6145", "Failed",    
    true(), "Unknown"
)
```
- In this example, EventCode is being "Translated" into a more readable format, where it displays "Success" or "Failed" based on the code EventCode normally returns

