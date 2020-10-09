1. 理解字符串前缀和后缀，abababca的前缀是[a,ab,aba,abab,ababa,ababab,abababc]，后缀是[bababca,ababca,babca,abca,bca,ca,a]
2. PMT(Partial Match Table)中的值是 当前子串 最长公共前后缀 长度
3. 如果是在 j 位 失配，那么影响 j 指针回溯的位置的其实是第 j −1 位的 PMT 值
4. 为了编程的方便， 我们不直接使用PMT数组，而是将PMT数组向后偏移一位，为next数组

```c++
int KMP(char * t, char * p) 
{
	int i = 0; 
	int j = 0;
	while (i < strlen(t) && j < strlen(p))
	{
		if (j == -1 || t[i] == p[j]) 
		{
			i++;
      j++;
		}
	 	else
    {
      j = next[j];
    }
  }
  if (j == strlen(p))
    return i - j;
  else 
    return -1;
}
```
1. i = 0， j = 0。确定主串和子串的起始位置。
2. 如果t[i] == p[j] 说明字符串是匹配的。所以i++,j++。两者位置都向前进1。
3. 如果不相等，则j = next[j] = pmt[j-1]
    pmt[j-1]为 字符串0~j-1长度的 前后公共子串，如果长度为x
    则0~x-1的位置不需要再比较，比较t[i]，p[x]的位置
    如果x == 0，则比较t[i]和p[0]的位置，如果不匹配，则j = next[0] = -1
    本质（将最长公共前缀直接移动到最长公共后缀的地方，从最长公共前缀的位置+1的位置开始匹配）。
4. 如果j = -1，说明上一次比较i和模式匹配子串0位置都不匹配。
    所以主串的位置需要往后移动一位。
    同时匹配串继续恢复到0的位置。


