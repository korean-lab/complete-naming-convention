# Gradle
## Dependencies
- When you add Library, you must include its URL.

DO:
```java
// BottomNavigationViewEx: https://github.com/ittianyu/BottomNavigationViewEx
implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.2'

// Circle Image View: https://github.com/hdodenhof/CircleImageView
implementation 'de.hdodenhof:circleimageview:3.0.0'
```
DO NOT:
```java
implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.2'
implementation 'de.hdodenhof:circleimageview:3.0.0'
```

- DO NOT USE + for the version.

DO:
```java
implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.2'
```
DO NOT:
```java
implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.+'
```
