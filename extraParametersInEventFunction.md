``` dart
 querySelector('#sample_text_id')
    ..text = 'Click me!'
    ..onClick.listen((MouseEvent e)=>randomStudentID("you!",e))
    ```
其中
``` dart
dowmStrudentID（“you！“,e)
```
定义为
```dart
void randomStudentID(String showStr,MouseEvent even){
 
}

```

这种用法在哪里能找到解释，请大家思考？特别留意``(MouseEvent e)=>``的用法。



{%ace edit=true, lang='dart'%}
// This is a hello world program for C.
#include <stdio.h>

int main(){
  printf("Hello World!");
  return 1;
}
{%endace%}