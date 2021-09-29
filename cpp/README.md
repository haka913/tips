# C++
## 목차
- [fast I/O](#fast-io)

- [메모리 초기화](#메모리-초기화)


## fast IO
10만 이상의 input, output시 cin,cout으로 입출력시 사용하면 된다.
단, 출력시 endl 대신 '\n'를 사용해야됨(사용하지 않으면 ?)
```c++
#include <iostream>
using namespace std;

int main(){
  ios::sync_with_stdio(0);
  cin.tie(0);
  cout.tie(0);
  // 위 아래 같은 방법
  ios::sync_with_stdio(false);
  cin.tie(NULL);
  cout.tie(NULL);
  return 0;
}
```

## 메모리 초기화
### memset(C)
int ch에는 1바이트(8bit)를 바꾸는 것이므로 0, -1이 아닌 다른 것을 넣게 되면
원하는 값으로 나오지 않는다.

int []에 5를 넣으면 32비트,4바이트에는
x0505 0505가 들어가 원하지 않는 값으로 들어가게 된다.

주로 0이나 -1 세팅시 사용하면 된다.


```C++
#include <cstring>
void* memset(void* str, int ch, size_t n);
int ar[5];
// ar 배열 0으로 세팅
memset(ar, 0, sizeof(ar));
```


### fill(C++)
메모리 초기화 다른 방법으로 fill이 있다.
val 채울 범위(first, end, val)로 채운다.

1차원의 경우 memset처럼 사용하면 되지만 2차원의 경우는 신경써줘야한다.

- #### 1차원 fill
```C++
#include <algorithm>
void fill(ForwardIterator first, ForwardIterator last, const T& val);
vector<int> v(5);
// vector 배열 3으로 세팅
fill(v.begin(),v.end(), 3);
```

- #### 2차원 fill
vector경우
fill(배열 행 시작, 배열 행 끝, (배열 열 길이,val));

배열 열 길이 다르게 주면 다르게 초기화 됨(5x5가 3으로 주게 되면 5x3으로 바뀜)

```C++
#include <algorithm>
void fill(ForwardIterator first, ForwardIterator last, const T& val);
vector<vector<int>> v(5,vector<int>(5));
// vector 2차원 배열 3으로 세팅
fill(v.begin(),v.end(), vector<int>(5,3));
```
